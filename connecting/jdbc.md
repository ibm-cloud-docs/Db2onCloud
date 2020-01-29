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

# Connecting programmatically with JDBC
{: #con_prog_jdbc}

Define a connection between a Java™ application and the {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

## Prerequisites
{: #prereq61}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

<!-- Before you can connect to your database, you must perform the following steps:

- [Verify prerequisites](prereqs.html), including installing driver packages, configuring your local environment, and downloading SSL certificates (if needed)
- Collect [connection information](credentials.html), including database details such as host name and port numbers, and connection credentials such as user ID and password -->

## Procedure
{: #proc61}

In each Java application, specify the user ID and password by including the **DriverManager.getConnection** method, and then include one of the following JDBC URL strings:

- For a connection with SSL:

  `jdbc:db2://<host_name>:50001/BLUDB:sslConnection=true;`

- For a connection without SSL:

  `jdbc:db2://<host_name>:50000/BLUDB`


