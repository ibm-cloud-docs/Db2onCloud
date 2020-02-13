---

copyright:
  years: 2014, 2020
lastupdated: "2020-02-13"

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

# SSL connectivity
{: #ssl_support}

The {{site.data.keyword.Db2_on_Cloud_short}} database uses a certificate for SSL connections that is issued by a third-party digital certificate authority (CA). 
{: shortdesc}

The CA certificate is part of the Db2 driver package. If your application connects with a driver from the Db2 driver package, you do not need to download the certificate separately. You can download the Db2 driver package from the web console.

However, if your application has its own driver, you might need to download the certificate separately. You can download the certificate from the web console.

Secure Sockets Layer (SSL) is a security protocol that provides communication privacy. SSL enables client and server applications to communicate in a way that is designed to prevent eavesdropping, tampering, and message forgery. SSL-enabled client applications use standard encryption techniques to help ensure secure communication.

Configuring your applications to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database with SSL depends on your company policy. Both the standard and the SSL protocols that you can use to connect to the database transmit user names and passwords as encrypted data. If you want to ensure complete end-to-end security, transmit all database information, including sensitive data and metadata, through an SSL connection. 

To enforce SSL connections, log in to the {{site.data.keyword.Db2_on_Cloud_short}} web console as an administrator, navigate to the **About** page, and select the **Enforce SSL connections** setting.
{: important}

<!-- SSL connections to {{site.data.keyword.Db2_on_Cloud_short}} are enforced by default. To enable a non-SSL port on your {{site.data.keyword.cloud_notm}} system, open a [support case](https://cloud.ibm.com/unifiedsupport/cases/add){:external} to make that request. -->

## Configuring your Db2 client
{: #ssl_cfg_client}

1. [Download the IBM Global Security Kit (GSKit)](https://www-945.ibm.com/support/fixcentral/swg/selectFixes?parent=Security+Systems&product=ibm/Tivoli/IBM+Global+Security+Kit&release=All&platform=All&function=fixId&fixids=8.0.*&source=fc){: external} by selecting the GSKit appropriate for your operating system (OS).

2. Download the SSL certificate from the **Connection Information** section of the {{site.data.keyword.Db2_on_Cloud_short}} web console. Store the SSL certificate file in a directory that can be referenced in a subsequent command.

3. Install the GSKit. See the following links for instructions:
   - [AIX](http://www-01.ibm.com/support/docview.wss?uid=swg21577384){: external}

   - [LINUX](http://www-01.ibm.com/support/docview.wss?uid=swg21631460){: external}

   - [WINDOWS](http://www-01.ibm.com/support/docview.wss?uid=swg21631462){: external}

   For more details, see [IBM Global Security Kit global installation instructions overview](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.swg.tivoli.gskit.install.doc/doc/c0055521.html){: external}

4. Set environment variable paths:

   - AIX: **LIBPATH**
     `/usr/opt/ibm/gsk8/lib`

   - Linux: **LD_LIBRARY_PATH**
     `/usr/local/ibm/gsk8/lib`

   - UNIX: **LD_LIBRARY_PATH**
     `/opt/ibm/gsk8/lib`

   - Windows: **PATH**
     `<installation_directory>\gsk8\bin`
     `<installation_directory>\gsk8\lib`  (`lib64` for GSKit 64-bit)

5. Create keystore. The following example command pertains to Windows:
   ```
   gsk8capicmd_64 -keydb -create -db "mykeystore.kdb" -pw "passw0rd" -stash
   ```
   {: codeblock}

   You must have the ability to write to the directory or you will get an error.
   {: note}

6. Add SSL certificate to the keystore. The following example command pertains to Windows:
   ```
   gsk8capicmd_64 -cert -add -db “mykeystore.kdb” -pw “passw0rd” -label ACIBLUDB_SSL -file c:\ssl\ACI_DigiCertGlobalRootCA.crt
   ```
   {: codeblock}

7. Update the Db2 database manager. The following example command pertains to Windows: 
   ```
   db2 update dbm cfg using SSL_CLNT_KEYDB c:\PROGRA~1\IBM\gsk8\mykeystore.kdb
   ```
   {: codeblock}

   On Windows, `Program Files` must use `PROGRA~1`.
   {: note}

## Connecting to your database
{: #ssl_conn_db}

1. [Optional] If you use Data Studio, you can now connect to the database by selecting port `50001` and `sslConnection=true`.

2. Catalog the node and database. The following example commands pertain to Windows:
   ```
   db2 catalog tcpip node ACICLD_S remote <IP_address_of_BLUDB_database_server> server 50001 security SSL
   ```
   {: codeblock}

   ```
   db2 catalog db BLUDB as ACIBLU_S at node ACICLD_S
   ```
   {: codeblock}

3. Connect to your database with an SSL connection. The following example commands pertain to Windows:
   ```
   db2 terminate
   ```
   {: codeblock}

   ```
   db2 connect to ACIBLU_S user <user_name>
   ```
   {: codeblock}


For more information, see [Configuring Secure Sockets Layer (SSL) support in non-Java Db2 clients](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.admin.sec.doc/doc/t0053518.html){: external}.

