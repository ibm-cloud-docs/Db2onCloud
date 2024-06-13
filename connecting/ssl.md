---

copyright:
  years: 2014, 2020
lastupdated: "2020-10-06"

keywords:

subcollection: Db2onCloud

---

 
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# SSL connectivity
{: #ssl_support}

The {{site.data.keyword.Db2_on_Cloud_short}} database uses a certificate for SSL connections that is issued by a third-party digital certificate authority (CA). 
{: shortdesc}

The CA certificate is part of the Db2 driver package. If your application connects with a driver from the Db2 driver package, you do not need to download the certificate separately. You can download the Db2 driver package from the web console.

However, if your application has its own driver, you might need to download the certificate separately. You can download the certificate from the web console.

Secure Sockets Layer (SSL) is a security protocol that provides communication privacy. SSL enables client and server applications to communicate in a way that is designed to prevent eavesdropping, tampering, and message forgery. SSL-enabled client applications use standard encryption techniques to help ensure secure communication.





## Configuring your Db2 client
{: #ssl_cfg_client}

The IBM [Global Security Kit (GSkit) ships with Db2 release 9.5 and later](https://www.ibm.com/support/pages/gskit-versions-shipped-db2){: external}. However, if the GSKit needs to be downloaded and configured, see [Configuring GSKit](#ssl_cfg_gskit).

1. Download the SSL certificate from the web console into a new directory:

   ```
   db2inst1@macing1:/home/db2inst1> mkdir SSL
   db2inst1@macing1:/home/db2inst1> cd SSL
   db2inst1@macing1:/home/db2inst1/SSL>
   ```
   
1. Create keystore in the SSL directory. The following example command pertains to Linux:
   ```
   gsk8capicmd_64 -keydb -create -db "mykeystore.kdb" -pw "passw0rd" -stash
   ```
   {: codeblock}

   You must have the ability to write to the directory or you will get an error.
   {: note}

1. Add SSL certificate to the keystore. The following example command pertains to Linux:
   ```
   gsk8capicmd_64 -cert -add -db "mykeystore.kdb" -pw "passw0rd" -label ACIBLUDB_SSL -file /home/db2inst1/SSL/DigiCertGlobalRootCA.crt
   ```
   {: codeblock}

1. Update the Db2 database manager. The following example command pertains to Linux: 
   ```
   db2 update dbm cfg using SSL_CLNT_KEYDB /home/db2inst1/SSL/mykeystore.kdb
   db2 update dbm cfg using SSL_CLNT_STASH /home/db2inst1/SSL/mykeystore.sth
   ```
   {: codeblock}



## Connecting to your database
{: #ssl_conn_db}

The hostname, port, user_name, and password of the `<BLUDB_database_server>` can be found in the [**Service credentials**](/docs/Db2onCloud?topic=Db2onCloud-connect_options){: external} for the service in the {{site.data.keyword.cloud_notm}} Console.



1. Catalog the node and database. The following example commands pertain to Linux:
   ```
   db2 catalog tcpip node ACICLD_S remote <hostname_of_BLUDB_database_server> server <port_of_BLUDB_database_server> security SSL
   ```
   {: codeblock}

   ```
   db2 catalog db BLUDB as ACIBLU_S at node ACICLD_S
   ```
   {: codeblock}

1. Connect to your database with an SSL connection. The following example commands pertain to Linux:
   ```
   db2 terminate
   ```
   {: codeblock}

   ```
   db2 connect to ACIBLU_S user <user_name> using <password>
   ```
   {: codeblock}

For more information, see [Configuring Secure Sockets Layer (SSL) support in non-Java Db2 clients](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.admin.sec.doc/doc/t0053518.html){: external}.

## Configuring GSKit
{: #ssl_cfg_gskit}

1. [Download the IBM Global Security Kit (GSKit)](https://www-945.ibm.com/support/fixcentral/swg/selectFixes?parent=Security+Systems&product=ibm/Tivoli/IBM+Global+Security+Kit&release=All&platform=All&function=fixId&fixids=8.0.*&source=fc){: external} by selecting the GSKit appropriate for your operating system (OS).

1. Download the SSL certificate from the **Connection Information** section of the {{site.data.keyword.Db2_on_Cloud_short}} web console. Store the SSL certificate file in a directory that can be referenced in a subsequent command.

1. Install the GSKit. See the following links for instructions:
   - [AIX](http://www-01.ibm.com/support/docview.wss?uid=swg21577384){: external}

   - [LINUX](http://www-01.ibm.com/support/docview.wss?uid=swg21631460){: external}

   - [WINDOWS](http://www-01.ibm.com/support/docview.wss?uid=swg21631462){: external}

   For more details, see [IBM Global Security Kit global installation instructions overview](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.swg.tivoli.gskit.install.doc/doc/c0055521.html){: external}

1. Set environment variable paths:
   - AIX: **LIBPATH**
     `/usr/opt/ibm/gsk8/lib`

   - Linux: **LD_LIBRARY_PATH**
     `/usr/local/ibm/gsk8/lib`

   - UNIX: **LD_LIBRARY_PATH**
     `/opt/ibm/gsk8/lib`

   - Windows: **PATH**
     `<installation_directory>\gsk8\bin`
     `<installation_directory>\gsk8\lib`  (`lib64` for GSKit 64-bit)


