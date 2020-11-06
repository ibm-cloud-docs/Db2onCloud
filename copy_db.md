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

The Copy Database feature in the {{site.data.keyword.Db2_on_Cloud_short}} service copies a database from one service instance to a new service instance. To use this feature, a backup of the current database must exist.

## Copying a running instance

### Select a backup
To copy your instance to a new service instance
1. select `Administration` from the menu on the left
2. select `Backup` from the tab on the top
3. select a backup to copy to a new instance
4. click on `Clone`

![Select a backup to Copy](images/cloning_select.png "Select a backup to copy"){: caption="Figure 1. Select a backup to copy to a new instance" caption-side="bottom"}

### Creating the new copy instance
Enter information for the new copy instance
1. select the datacenter for the new copy instance under `Datacenter location`
2. enter a name for under `Service name`
3. select the resource group of the new instance under `Resource group`
4. pick `High availibity configuration`
5. select a `Pricing plan`
6. click on `Clone`


![Create the new copy](images/cloning_new_instance.png "Create the new copy"){: caption="Figure 2. Create a new copy instance" caption-side="bottom"}

### Progress
The notifications icon on the top right of the console will show the progress of the copy

![Copy rogress](images/cloning_progress.png "Copy progress"){: caption="Figure 3. Copy progress" caption-side="bottom"}

### Copy Success
Once the copy has successfully completed, the notifications icon will display a success message.

![Copy success](images/cloning_success.png "Copy success"){: caption="Figure 4. Copy success" caption-side="bottom"}