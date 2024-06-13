---

copyright:
  years: 2014, 2023
lastupdated: "2023-07-31"

keywords:

subcollection: Db2whc

---

# Command syntax for LOGICAL BACKUP and LOGICAL RESTORE 

## Authorization 

All following authorities and permissions are required to execute **LOGICAL_BACKUP** stored procedure:

1. EXECUTE privilege on SYSPROC.LOGICAL_BACKUP procedure (default NOT granted to PUBLIC)
2. One of the following to access table data:
    - DATAACCESS authority on the database or schema 
    - SELECTIN privilege on the schema
    - SELECT privilege on all tables in the schema
3. In case one or more tables in the schema have Row and Column access (RCAC) controls enabled
    - LOGICAL BACKUP AND RESTORE OF RCAC PROTECTED DATA privilege on the schema
        - Note: As with any privilege, user is not able to grant permissions to the same user. However, it possible to grant privilege to group or role that the user is part of.
        - E.g. bluadmin user is not able to grant that privilege to bluadmin user, but can to  bluadmin group

4. EXECUTE permission on the following procedures: 
    - SYSPROC.ADMIN_GET_DEPTREE
    - SYSPROC.WLM_SET_CLIENT_INFO
    - SYSPROC.MONITOR_UTIL
    - SYSPROC.ADMIN_SET_MAINT_MODE

All following authorities are required to execute **LOGICAL_RESTORE** stored procedure:

1. EXECUTE privilege on SYSPROC.LOGICAL_RESTORE procedure (default NOT granted to PUBLIC)
2. In case of a schema restore and **drop-existing** option
    - SCHEMAADM authority on the schema
3. One of the following to drop/create tables in schema
    - SCHEMAADM authority on the schema
    - DROPIN and CREATEIN authority on the schema
4. INSERTIN authority to populate table data
5. In case of restoring incremental/delta backup image
    - ALTERIN, DELETEIN, SELECTIN authority on the schema
6. In case one or more tables in the schema have Row and Column access (RCAC) controls enabled
    - LOGICAL BACKUP AND RESTORE OF RCAC PROTECTED DATA privilege on the schema
        - Note: As with any privilege, user is not able to grant permissions to the same user. However, it possible to grant privilege to group or role that the user is part of.
        - E.g. bluadmin user is not able to grant that privilege to bluadmin user, but can to bluadmin group

7. EXECUTE permission on the following procedures:
    - SYSPROC.ADMIN_DROP_SCHEMA
    - SYSPROC.WLM_SET_CLIENT_INFO
    - SYSPROC.MONITOR_UTIL
    - SYSPROC.ADMIN_SET_MAINT_MODE

All following authorities are required to execute **LOGICAL_BACKUP_DETAILS** stored procedure: EXECUTE privilege on SYSPROC.LOGICAL_BACKUP_DETAILS procedure (default NOT granted to PUBLIC)

Backup images created using -path option will be owned by the connected user (top folder, all sub-folders, and all files).

## Required connection 

Implicit or explicit 

## Command syntax for LOGICAL_BACKUP 

Schema-level backup can be performed by passing the schema name to the LOGICAL_BACKUP stored procedure using -schema option. On error partial backup image will be removed. On success timestamp is returned as part of return sqlcode. This timestamp is to be used as a label to refer to the backup image, e.g. to restore it. Logical backup ensures that timestamp is unique in case when several backups are started at the same time.

When using this command in a cloud environment, do not use the -path or -tsm option, and do not specify any -errorlogdir path. You are unable to view local files on the server hosting the instance. 
{: important}

![](syntax_diagram1.png)

Handling for different table types under schema backup:

- External Tables – The definition of the external table will be captured and restored but not the contents.

- Materialized query tables - The definition of the MQT will be captured and restored but not the contents. The user will need to refresh the MQT after restore.

- Temporary tables – These are not captured by schema backup.

- Any permanent tables not organized by column will cause schema backup of a schema enabled for row modification tracking to fail (since these tables would not be enabled for row modification tracking).

## Command syntax for LOGICAL_RESTORE 

Schema level restore can be performed by passing the schema name to the LOGICAL_RESTORE stored procedure using -schema option. To restore a single or multiple tables, -table or -tablefile options can also be used respectively.

![](syntax_diagram2.png)

## Command syntax for LOGICAL_BACKUP_DETAILS 

The stored procedure returns a list of timestamp labels that are available on a specified path/media. By default EXECUTE permission is granted to PUBLIC.

![](syntax_diagram3.png)

## Command parameters 

Cloud clients should not set this parameter as they are unable to access the file on the server.
{: important} 

-type FULL|INC|DEL
    - **FULL** – Full backup.
    - **INC** – Cumulative incremental backup.
    - **DEL** – Delta incremental backup (also known as a differential backup).

-schema SCHEMANAME
Schema to be backed up. Multiple schema names must be separated by space.
-path <path>
    Target directory for backup image. Mutually exclusive with **-tsm**, **-s3** and **-cos** options. Multiple paths strings must be separated by space. Must point to different mount points. Backup directory and files are owned by the user that invoked logical backup. Subject to **extbl_strict_io** and  **extbl_location** configuration parameters.
-tsm
    Backup image is to be stored in IBM Spectrum Protect server. Mutually exclusive with **path** and **s3** options.
-s3
    Backup image is to be stored in S3 cloud. Mutually exclusive with **-path**, **-tsm**, and **-cos** options. **-bucket_url**, **access-key**, **-secret-key**, and either **-default-region** or **-endpoint** options are mandatory. If both **-default-region** and **-endpoint** are specified, then region in -endpoint must match one in **-default-region**. Data is sent directly to cloud, no local temp storage is required.
-cos
    Backup image is to be stored in IBM COS. Mutually exclusive with **-path**, **-tsm**, and **-s3** options. **-bucket_url** **-access-key**, **-secret-key**, and **-endpoint** options are mandatory. If specified, **-default-region** is ignored. Data is sent directly to cloud, no local temp storage is required.
-errorlogdir <path>
    Path (on server) where diagnostic log files will be saved to. Default is **sqllib/tmp/bnr/logs** subject to **extbl_strict_io** and **extbl_location** configuration parameters.

> **Note: Cloud clients should not set this parameter as they are unable to access the file on the server.** 

-keeplogs {on_error | summary_in_backup | all_in_errorlogdir}
    On failure all diagnostic log files are preserved. The option indicates how diagnostic log files are to be handled after a successful operation. -keeplogs **on_error** - remove all diagnostic log files. **summary_in_backup** - save the main tracelog to the backup image (becomes part of the backup image). Default for **s3**, **cos**, and **tsm**. **all_in_errorlogir** - preserve all diagnostic log files in errorlogidr. Default for **path**.
**-sessions <N>(optional)**      
    Spawns N threads/connections to backup individual tables concurrently. Default value is 4. For multi-schema backups N threads are spawned for each schema.
**-compress NO|GZIP|LZ4 (optional)**
    Compress setting for the backup. By default, it is set to **LZ4**.
**-format TEXT|BINARY (optional)** 
    Format for the backup files. By default, it is set to **BINARY**.
**-media-connection-timeout <milliseconds>(optional)**
    Maximum time (in milliseconds) to wait before TSM, S3 or IBM COS connection timeout.
-bucket-url <bucket-url>
    URL of the cloud bucket.
-access-key <access-key>
    Access key id for the bucket.
-secret-key <secret-key>
    Secret access key for the bucket.
-default-region <region>
    Default region of the bucket.
-endpoint
    Gateway endpoint that connects to either Amazon S3 or IBM COS. If both **-default-region** and **-endpoint** are specified, then region in **-endpoint** must match one in **-default-region**.
-multipart-size-mb <multipart size mb>
    Value (in MB) of -multipart-size-mb. Default is 105.
-delete-backup
    Permanently remove backup image. Requires path/media and timestamp to be provided. Cannot be specified in conjunction with **-type** or **-schema**
**-table <table> (optional)**
    Table to be restored. Table must not exist, or -drop-existing option must be specified.
**-target-schema name (optional)**
    Restore backup image using different schema name without dropping original schema. **-drop-existing** affects new schema name.
**-drop-existing (optional)**
    Drop existing schema and its table/non-table objects before restore. If used in conjunction with -table option, only affected table is dropped.
-keep-rcac
    Restore RCAC-enabled tables, masks, and permissions without dropping them.
-replace-rcac
    Restore RCAC-enabled tables, masks, and permissions by dropping and recreating them.
**-enable-row-mod-tracking (optional)**
    Restores a schema backup image taken from schema not enabled for row modification tracking and enables target schema for row modification tracking.
**image-check HASH, SIZE, NAME, NONE, ONLY (optional)**
    For backup: post-process schema backup image files after backup operation to enable image integrity verification prior to schema-level restore. Both values can be selected. Neither is on by default. Information to verify NAME option (list of names of all files in the backup image) is always collected.

    For restore: validate schema backup image prior to restore. By default all options specified during backup are enabled (including implicit NAME). Only specified options will be validated. Validation for options not collected during backup will be silently ignored.

- **HASH** - compute and record hash values for all files in backup image. Only allowed for `-path` backups.
- **SIZE** - record sizes of all files in backup image.
- **NAME** - identify missing or unexpected file names.
- **NONE** - do not perform any integrity checks.
- **ONLY** - perform integrity checks only without invoking restore (validate backup image).

**-unlockschema (optional)**
    Unlock schema after a failed restore. Does not complete previously failed operation.
**-cleanup-failed-restore (optional)**
    Cleanup after a failed restore. Drops all objects and schema itself. In case schema cannot be dropped it is still unlocked.
**-backup-migrate (optional)**
    Take logical backup of a schema that is not yet enabled for row modification tracking to facilitate upcoming restore with **-enable-row-modification-tracking** Backup will fail if source tables are not be possible to be row modification tracking, for example organize by row. Only allowed for **-type** FULL operation. 

## New sqlcodes 

On success of LOGICAL_BACKUP() SQL1796I will be returned. E.g.: 

<pre>
SQL1796I  Logical backup utility has completed successfully, timestamp for the
backup image is "20220817203500".  SQLSTATE=01541
<pre>

On success of LOGICAL_RESTORE() sqlcode 0 will be returned.

<pre>
 $ db2 "call sysproc.logical_restore('-type frh -schema rmt  -timestamp 20220902105215 -s3 ...

  Return Status = 0
<pre>

On success of LOGICAL_BACKUP_DETAILS() table with list timestamps will be returned: 

<pre>
$ db2 call SYSPROC.LOGICAL_BACKUP_DETAILS('-path ...')


 Result set 1
 --------------

 TIMESTAMP
 --------------------
 20220805182316

 1 record(s) selected.

 Return Status = 0

 <pre>

On failure of either LOGICAL_BACKUP(), LOGICAL_RESTORE(), or LOGICAL_BACKUP_DETAILS() SQL1797 will be returned. E.g.:

<pre>
SQL1797N The "SYSPROC.LOGICAL_RESTORE" utility has failed with error "Valid path required". SQLSTATE=5UA0Q
<pre>
