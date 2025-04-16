---

copyright:
  years: 2014, 2025
lastupdated: "2025-04-12"

keywords: 

subcollection: Db2onCloud

---

<!-- Attribute definitions --> 
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# Deleting a database
{: #del_db}

When a service instance is deleted, the database that it provides is also removed. This will delete any online data and logs as well as database backups. The data will not be recoverable after this action.

## How is the data deleted
{: #del_db_how}

All data is encrypted at rest to ensure data is protected at all times using encryption keys stored in a key management service called Key Protect. When access to those keys is removed, the data is crypto-shredded and cannot be recovered. When the service instance is deleted, the block storage that is used for the database is wiped to ensure that all of the data is erased. Any data objects in cloud object storage are also deleted and not recoverable.

## When is the data deleted
{: #del_db_when}

## Using your own encryption keys to delete data
{: #del_db_keys}

You can use your own encryption keys to delete data. This is called crypto-shredding. After the key is deleted, your data is unrecoverable and unreadable by anyone.

Key Protect allows you to initiate a force delete of a key that is in use by various {{site.data.keyword.cloud}} services, including your {{site.data.keyword.Db2_on_Cloud_short}} service instances. Deleting a key that is in use on your deployment locks the disks containing your data when the key is requested again. You can have this occur right away by contacting IBM Support or by deleting your service instance. Key deletion is sent to the Log Analysis Activity Tracker as kms.secrets.delete.

If you delete a deployment that is protected with your Key Protect key, the deployment remains registered against the key for the duration of the soft-deletion period (up to 9 days). If you need to delete the key during the soft-deletion period, you have to force delete the key. After the soft-deletion period, the key can be deleted without the force. You can check the association between the key and your deployment to determine when you can delete the key.

## Deleting data in your database
{: #del_db_data}

The Db2 database stores data in pages on block storage. When **DELETE** or **TRUNCATE** operations are performed, that data is no longer accessible unless you are using `TEMPORAL` tables. The physical pages that contain the data are not immediately erased and might still exist on the disk, but will be overwritten as needed. There is no ability to recover this data. The database provides the **REORG** and **REDUCE MAX** capability to reclaim this space for other activities or it will be reused when the database needs to store more data.
