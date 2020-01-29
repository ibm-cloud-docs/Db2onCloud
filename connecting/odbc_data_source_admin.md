---

copyright:
  years: 2014, 2019
lastupdated: "2018-09-25"

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

# Connecting with the ODBC Data Source Administrator
{: #con_prog_odbc_dsa}

Use the Microsoft ODBC Data Source Administrator tool to define a connection between an ODBC or CLI application and a {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

## Prerequisites
{: #prereq91}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

<!-- Before you can connect to your database, you must perform the following steps:

- [Verify prerequisites](prereqs.html), including installing driver packages, configuring your local environment, and downloading SSL certificates (if needed)
- Collect [connection information](credentials.html), including database details such as host name and port numbers, and connection credentials such as user ID and password -->

## Procedure
{: #proc91}

1. Install the [Db2 driver package](/docs/Db2onCloud?topic=Db2onCloud-dr_pkg#dr_pkg).

2. Open ODBC Data Source Administrator and create either a User DSN or System DSN for the Db2 driver package.
    
3. Click **Advanced** Settings. Enter following CLI parameters with their values for the {{site.data.keyword.Db2_on_Cloud_short}} server: **Hostname**, **Port**, and **Database**.
    
4. For an SSL connection, enter CLI parameter **Security** with value `SSL`.
    
5. Click **Apply**.
    
6. To test the connection, return to main page of ODBC Data Source Administrator. Click **Configure** for the DSN that you created. Enter the user ID and password for the server and click **Connect**.

