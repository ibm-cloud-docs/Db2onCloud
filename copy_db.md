---

copyright:
  years: 2014, 2019
lastupdated: "2019-11-18"

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

# Copy Database
{: #cp_db}

The {{site.data.keyword.Db2_on_Cloud_long}} Copy Database feature gives you the ability to copy your existing database with ease. 
{: shortdesc}

The following examples are helpful use cases for using a copy of a database:
- Run analytics or reports
- Make a fresh copy of your production database each morning to use for development purposes
- Make a *template* database for an app, and make a copy of that template as your apps need it

## Prerequisites
{: #cp_prereqs}

The Copy Database feature in the {{site.data.keyword.Db2_on_Cloud_short}} service copies a database from once service instance to another, overwriting everything on the target service instance. In order to use the feature, both the source and target {{site.data.keyword.Db2_on_Cloud_short}} service instances must already exist and be in a resource group. In addition, if your {{site.data.keyword.Db2_on_Cloud_short}} service instance is a Cloud Foundry service, you must migrate your service instance and apps to a resource group. For information about the migration, see [Migrating Cloud Foundry service instances and apps to a resource group](/docs/resources?topic=resources-migrate#migrate).

