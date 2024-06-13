---

copyright:
  years: 2014, 2023
lastupdated: "2023-08-01"

keywords: 

subcollection: Db2whc

--- 

# Schema-level and table-level backup and restore


You can use the Db2 logical schema backup and restore features to do full, cumulative incremental, or delta incremental backups of a schema, followed by full restore of the schema or one or more tables within the schema. 

The [LOGICAL BACKUP](https://www.ibm.com/docs/en/db2/11.5topic=procedures-logical-backup-stored-procedure) and [LOGICAL RESTORE](https://www.ibm.com/docs/en/db2/11.5?topic=procedures-logical-restore-stored-procedure) stored procedures provide a flexible and lightweight way to backup and restore table-level data. While the LOGICAL BACKUP stored procedure does not capture database-level objects, it does support the following schema backup options:

**Full**
    Creates a copy of a selected database schema and all table data within the schema
**Cumulative incremental**
    Creates a copy of all database data that has changed in a selected schema since the most recent successful, full backup operation.
**Delta incremental**
    Creates a copy of all database data that has changed in a selected schema since the most recent successful backup operation of any type.

Full and incremental schema level backups provide you with read and concurrent insert, update, and delete access to tables in the schema. {: Note}

## Row modification tracking for column-organized tables

If you are backing up a column-organized schema that is used for analytic workloads, then you need to [enable row modification tracking](https://www.ibm.com/docs/en/db2/11.5?topic=SSEPGG_11.5.0/com.ibm.db2.luw.admin.dbobj.doc/doc/t_enable_log_schema_bckup_restore.htm) on your target schema. You enable row modification tracking on a column-organized target schema by including the ENABLE ROW MODIFICATION TRACKING clause as part of a [CREATE SCHEMA](https://www.ibm.com/docs/en/db2/11.5?topic=statements-create-schema#r0000925__create_enable_row_mod_trak) operation. You can also modify an existing schema by adding the clause to an [ALTER SCHEMA](https://www.ibm.com/docs/en/db2/11.5?topic=statements-alter-schema#r0058662__row_mod_trak) statement. Once this is done, any table that is created within your target schema is created with row modification tracking enabled. This setting enables the logical schema backup feature to capture table data from column-organized tables.

Row modification tracking is not enabled by default. To take advantage of the incremental schema backup and restore, explicit schema creation using the ENABLE ROW MODIFICATION TRACKING clause is necessary. {: Note}

## Limitations for Db2 objects in a schema where row modification tracking is enabled

- [Exception tables](https://www.ibm.com/docs/en/db2/11.5?topic=tables-exception) for [db2load](https://www.ibm.com/docs/en/db2/11.5?topic=apis-db2load-load-data-into-table) and [INGEST](https://www.ibm.com/docs/en/db2/11.5?topic=tasks-ingesting-data) operations cannot be column-organized. Instead, create a row-organized exception table in a separate schema. This table causes the incremental schema backup to fail. Also, the row-organized exception table must have a similar definition to the column-organized table that is configured for row modification tracking. The exception is the SYSROWID column, which cannot be an identity column since these are not supported in exception tables. For example:
* CREATE SCHEMA S1 ENABLE ROW MODIFICATION TRACKING
* CREATE SCHEMA S2
* CREATE TABLE S1.T1 (C1 INT)
* CREATE TABLE S2.LOADEXTBL (SYSROWID BIGINT NOT NULL, CREATEXID BIGINT NOT NULL, DELETEXID BIGINT NOT NULL, C1 INT)
* LOAD FROM <file> OF DEL INSERT INTO S1.T1 FOR EXCEPTION S2.LOADEXTBL
- The maximum number of user defined columns in a table enabled for row modification tracking is reduced to 1009.
- IMPORT using CREATE or REPLACE_CREATE options into a table enabled for row modification tracking may fail.
- ADMIN_COPY_SCHEMA with a **copymode** of ‘COPY’ or ‘COPYNO’ will fail if at least one table is defined as DISTRIBUTE BY RANDOM or contains GENERATED ALWAYS AS IDENTITY column.
- No support for alter of a table enabled for row modification tracking to be a materialized query table.
- None of the three new hidden columns (SYSROWID, CREATEXID, DELETEXID) are supported within the distribution key of the table (this means they are not allowed in the DISTRIBUTE BY HASH column list).
- No support for **db2move** if the source or target is a table in a schema enabled for row modification tracking.
- None of the three new hidden columns can be included as part of an index key or in an enforced constraint.
- No support for System-period temporal tables or Bitemporal-period tables with row modification tracking enabled, however Application-period temporal table will support row modification tracking.
- No support for CREATE VIEW … WITH ROW MOVEMENT with row modification tracking enabled.
- REORG TABLE … RECLAIM EXTENTS reclaims space from deleted SYSROWID/CREATEXID/DELETEXID columns. Space is reclaimed only for rows that were deleted prior to last **-type ONL** (full schema) backup.

## Dealing with failed backup and restore operations 

When a logical schema backup or restore operation fails, the first source of information about the error is the sqlca message. For example, the following error message indicates that the schema to be backed up contains a table that is not enabled for row modification tracking:

'''

SQL1797N  The "SYSPROC.LOGICAL_BACKUP" utility has failed with error "non-RMT
table "T3".".  SQLSTATE=5UA0Q

'''

If the message is not clear, or ambiguous from being cropped, the next point of information is the tracelog file. It is stored in the path that is prefixed by the path that is provided as the -errorlogdir option or sqllib/tmp/bnr/logs by default. The path is appended with a subfolder named for the approximate timestamp for when the failed operation was run. For example: /home/db2inst1/sqllib/tmp/bnr/logs/20221110202644

This timestamp is not to be confused with the timestamp that is used for the backup image. {: Attention}

The folder can contain the following types of log files:

- External table log files.
- Connector log files (communication with external media: IBM Spectrum Protect, AWS S3, or IBM COS).
- The backup or restore tracelog file.
- The backup or restore log file. This file is a concise version of tracelog file.

## Migration considerations 

Enabling row modification tracking on a schema does not modify any of the tables in the schema: Only new tables created in the schema are enabled for row modification tracking. For a logical schema backup to be restored successfully, all columnar tables in the target schema must be recreated after the schema is enabled for row modification tracking. 

![](syntaxdiagram_enr_5jl_4vb)

**Table migration**
    Recreating tables can be done through any means. For example, you can recreate tables in your target schema by running an ADMIN_MOVE_TABLE, or CREATE TABLE … AS … WITH DATA statement. Simply select * from one table into a new table in the same schema. The target table is created as enabled for row modification tracking so long as the following conditions exist:
    - The target schema is enabled for row modification tracking
    - The target table type supports row modification tracking.

The source table does not need to have row modification tracking enabled. Also, remember that attempting to move any of the hidden columns from a source table to a target table results in an error, as the hidden columns already exist in the row-modification-tracking-enabled target table. Values for the new hidden columns are not carried over from the source to the target during a CREATE TABLE … AS (fullselect) WITH DATA operation.

**Table data migration using logical backup and restore**
    To assist with migration, SYSPROC.LOGICAL_BACKUP is able to take logical backup image of a schema that is not enabled for row modification tracking by specifying -backup-migrate option. Please note that for the whole duration of this backup only read access is allowed to tables in the schema. Once backup is done, it is possible to restore backup image using SYSPROC.LOGICAL_RESTORE(-enable-row-modification-tracking) option. In that case schema is created as ENABLE ROW MODIFICATION TRACKING, and all tables in the schema are attempted to be enabled as well. Any table DDL/condition in original schema that will prevent table from being enabled for row modification tracking will cause the backup to fail.

- [**Monitoring logical schema backup and restore operations**](https://www.ibm.com/docs/en/db2/11.5?topic=restore-monitoring-logical-schema-backup-operations)
You can monitor the progress of logical schema backup and restore operations when using the stored procedures to capture and restoring Db2 table-level data.
- [**Limitations of schema-level backup when working with columnar data**](https://www.ibm.com/docs/en/db2/11.5?topic=restore-logical-backup-logical-limitations)