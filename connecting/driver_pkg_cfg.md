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

# Configuring your local environment
{: #cfg_loc_env}

To connect local applications and tools to your {{site.data.keyword.Db2_on_Cloud_short}} database, you need to configure your environment.  
{: shortdesc}

## Prerequisites
{: #prereq21}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

<!-- 1. Install the Db2 driver package for your operating system.

   - [Installing on Windows](install_win.html)
   - [Installing on Linux or PowerLinux](install_linux.html)
   - [Installing on Mac OS X](install_mac.html)
2. Decide whether or not you will be using Secure Sockets Layer (SSL) to connect to your database.
3. Collect database details and connect credentials, including the host name of your server, and your database user ID and password. -->

## Procedure
{: #proc21}

1. Add entries to the driver configuration file, `db2dsdriver.cfg`, for your database.

   The configuration steps are different depending on whether you want to connect to your database by using SSL:

   **With SSL**

   To connect your applications and tools to your database by using SSL, enter the following commands in a command shell on Linux operating systems, at the Windows command prompt, or in a Db2 command window: 

   `db2cli writecfg add -database BLUDB -host <hostname> -port 50001`

   `db2cli writecfg add -dsn <alias> -database BLUDB -host <hostname> -port 50001`

   `db2cli writecfg add -database BLUDB -host <hostname> -port 50001 -parameter "SecurityTransportMode=SSL"`

    where:

   - `<hostname>` is the host name of your server.
   - `<alias>` is an alias that you choose. The alias cannot be the same as the database name, `BLUDB`. If you want to have spaces in the alias, surround the alias with double quotation marks.

   **Without SSL**

   To connect your applications and tools to your database without using SSL, enter the following commands in a command shell on Linux operating systems, at the Windows command prompt, or in a DB2 command window: 

   `db2cli writecfg add -database BLUDB -host <hostname> -port 50000`

   `db2cli writecfg add -dsn <alias> -database BLUDB -host <hostname> -port 50000`

    where:

   - `<hostname>` is the host name of your server.
   - `<alias>` is an alias that you choose. The alias cannot be the same as the database name, `BLUDB`. If you want to have spaces in the alias, surround the alias with double quotation marks.

2. Test connecting by issuing the **db2cli validate** command from the command prompt:

   `db2cli validate -dsn <alias> -connect -user <userid> -passwd <password>`

   where: 
   
   - `<alias>` is an alias that you created with the **db2cli writecfg** command.
   - `<userid>` is your Db2 user ID.
   - `<password>` is your Db2 password.

3. (*Optional*): To be able to connect local ODBC applications and tools to your database, register the DSN with the ODBC driver manager:
 
   Run the following command from a command line: 

   `db2cli registerdsn -add -dsn <alias>`

   where: 

   - `<alias>` is an alias that you created with the **db2cli writecfg** command.

   By default, the DSN is created as a user DSN.

