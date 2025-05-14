---

copyright:
  years: 2014, 2025
lastupdated: "2025-01-20"

keywords:

subcollection: Db2onCloud

---


{:javascript: #javascript .ph data-hd-programlang='javascript'}
{:java: #java .ph data-hd-programlang='java'}
{:ruby: #ruby .ph data-hd-programlang='ruby'}
{:php: #php .ph data-hd-programlang='php'}
{:python: #python .ph data-hd-programlang='python'}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:video: .video}

# Getting started with {{site.data.keyword.Db2_on_Cloud_short}}
{: #getting-started}

You can provision an instance of IBM Db2 as a Service through the [IBM Cloud catalog](https://cloud.ibm.com/catalog/services/db2). Create a [free account](https://cloud.ibm.com/registration?target=%2Fcatalog%2Fservices%2Fdb2-warehouse) and get an IBM Cloud credit of $200 that you can use towards Db2 SaaS.

After creating the Db2 SaaS service, you can create a user name and password by clicking the **Service credentials** tab on your service page and selecting **New credential**.

While logged in as the **IAM** user that provisioned the instance, you can log into the web console by clicking on the **Go to UI** button on the **Manage** tab.

You can create database/JDBC users, which you will use to connect to the database, by navigating to the **Administration** --> **User Management** panel. Additionally, you may want to give admin access to an IAM user to allow them to use console administration functions such as user management, backup, and restore. Before you can add an IAM user in the console, you must first give the user access to the service in IAM". For more information, see [Identity and access management (IAM) on IBM Cloud](https://cloud.ibm.com/docs/Db2onCloud?topic=Db2onCloud-iam).
