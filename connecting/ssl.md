---

copyright:
  years: 2014, 2020
lastupdated: "2020-02-05"

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


