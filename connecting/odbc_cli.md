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

# Connecting programmatically with ODBC or CLI
{: #con_prog_odbc_cli}

Define a connection between a Microsoft Windows ODBC or CLI application and a {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

## Prerequisites
{: #prereq81}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

<!-- Before you can connect to your database, you must perform the following steps:

- [Verify prerequisites](prereqs.html), including installing driver packages, configuring your local environment, and downloading SSL certificates (if needed)
- Collect [connection information](credentials.html), including database details such as host name and port numbers, and connection credentials such as user ID and password -->

## Procedure
{: #proc81}

1. In a command shell on Linux operating systems, at the Windows command prompt, or in the Db2 command window on Windows operating systems, enter the following commands:

   **Note**: These commands create new entries in the driver configuration file (`db2dsdriver.cfg`) on your computer and set the connection attributes. You need to do this step only one time.
   
   - For a connection with SSL:

     `db2cli writecfg add -database BLUDB -host <hostname> -port 50001 -parameter "SecurityTransportMode=SSL"`

     `db2cli writecfg add -dsn <alias> -database BLUDB -host <hostname> -port 50001`

   - For a connection without SSL:

     `db2cli writecfg add -database BLUDB -host <hostname> -port 50000`

     `db2cli writecfg add -dsn <alias> -database BLUDB -host <hostname> -port 50000`

   where:

   `<hostname>` is the host name of the server

   `<alias>` is a DSN alias that you choose
    
2. (*Optional*): To test the connection to the database, run this command from the command prompt:

   `db2cli validate -dsn <alias> -connect -user <user_id> -passwd <password>`

   where:

   `<alias>` is the DSN alias that you created with the **db2cli writecfg** command

   `<user_id>` is from the connect credentials that you collected beforehand

   `<password>` is from the connect credentials that you collected beforehand

3. (*Optional*): To register the data source name (DSN) with Microsoft ODBC Driver Manager and to work with Microsoft ODBC applications, run the following command. By default, the DSN is created as user DSN.

   `db2cli registerdsn -add -dsn <alias>`

   where:
        
   `<alias>` is the DSN alias that you created with the **db2cli writecfg** command



