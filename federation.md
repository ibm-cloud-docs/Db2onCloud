---

copyright:
  years: 2014, 2019
lastupdated: "2019-05-31"

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

# Legacy Plan Data virtualization (federation)
{: #data_virt_fed}

Db2 data virtualization (also known as federation) is supported by {{site.data.keyword.Db2_on_Cloud_short}}. Data virtualization gives you single-query access to all of your data that is on multiple distributed databases anywhere in your organization. You can access data that is on any of your Db2 or Informix data sources, both in the cloud and on premises. 
{: shortdesc}

This function is supported on all versions of {{site.data.keyword.Db2_on_Cloud_short}}, except for the free Lite plan. However, you can use the Lite plan as a target from which you can pull data.

## Use Cases
{: #use_cases}

### Consolidate data sources

By federating your data sources that are located both in the cloud and on premises anywhere in your organization, your virtualized data appears to be retrieved from a single source. Data virtualization eliminates the burdensome and costly data migration process, giving you the ability to analyze all of your data efficiently and cost effectively.

<!-- A company may have started their operations with an on-premises Db2 server. As cloud technology becomes more widespread and companies start to operate on cloud in a cost-effective fashion, there will be continued Cloud growth. However, the organization’s data on both sources remain as a critical component to their decision-making processes. By way of example, a client operating in retail industry needs to be able to access all data, say customer information, to run further analysis on their customers’ consumption behaviors. They need to be able to identify customers, match their records on cloud with already existing ones from an on-premises database and compose them as if the data is being retrieved from a single source. Federation capability here prevents the burdensome data migration process and allows the user to access the data without moving the data.

located in the cloud and on-premises -->

### Attach to Db2 Warehouse on Cloud

Users of products in the Db2 family can federate data from {{site.data.keyword.Db2_on_Cloud_short}} and {{site.data.keyword.dashdbshort_notm}} databases. From a common interface to access the data, you can easily add, query, and analyze your data without complex ETL processes and without any additional code.

<!-- Db2 family users would now be able to federate data between Db2 on Cloud and Db2 Warehouse on Cloud. By being provided a common interface for accessing the data, a user can now easily add or query data from or to the Warehouse without complex ETL processes or any additional code. -->

### Sharded data across multiple servers

At times, you might choose to partition (shard) your data. With federation capabilities, sharded data can be queried with a unified interface. Federation gives you the ability to better balance your workloads, scale specific parts of an app, and create microservices that work together. 

<!-- At times, users may choose to partition (shard). With federation capabilities, data can be queried with a unified interface and this lets the user better balance the workload, scale specific parts of an app or create microservices that work together. -->

### Increase database capacity beyond fixed limits

Federation gives you the ability to increase the capacity of an on-premises database by federating with a database on the cloud. Data virtualization in this case is a great option if your on-premises database is running out of storage. Increasing the capacity of a database with federation is useful for new development because developers don't need to change a database already in production. You can also federate between two {{site.data.keyword.Db2_on_Cloud_short}} databases to increase the database capacity beyond the current limits of the Flex plan.

<!-- By using federation, users can increase capacity of an on premises database by federating to or from the cloud. This is a great option if your on premises database is running out of storage. Increased capacity will also be useful for new development as our users no longer need to change a database in production. You can also use this feature to federate between two Db2 on Cloud databases to increase the capacity beyond the current limits of the Flex plan. -->

## Getting started
{: #getting_started_fed}

The following steps are an example of how you go about federating your disparate data sources to appear as if the data is retrieved from a single source. The following example illustrates the federation of two {{site.data.keyword.Db2_on_Cloud_short}} databases:

### On the Db2 on Cloud target machine
{: #targ}

Host name: targetdotcom

1. Create a table `testdata` in schema `admin2`.

2. From the {{site.data.keyword.Db2_on_Cloud_short}} console, load the `testdata` table with data as user `admin2` with password `YYYY`.

<!-- ### On a client machine of the target

1. Catalog the target machine:<br/>
   `db2 catalog tcpip node <node_name> remote <host_name> server 50000`<br/>

   For example:<br/>
   `db2 catalog tcpip node fedS remote targetdotcom server 50000`

2. Catalog the database on fedS:<br/>
   `db2 catalog db bludb as <db_name> at node <node_name>`

   For example:<br/>
   `db2 catalog db bludb as srcdb at node fedS`

3. Connect to the database on fedS:<br/>
   `db2 connect to <catalog_db_name> user <admin_user> using '<admin_password>'`

   For example:<br/>
   `db2 connect to srcdb user 'admin1' with password 'XXXX'`

4. Create a wrapper on fedS:<br/>
   `db2 "create wrapper drda"`

5. Create a server to talk to the target machine:<br/>
   `db2 "create server <server_name> type dashdb version 11 wrapper drda authorization \"<admin_user_on_target>\" password \"<admin_password_on_target>\" options (host '<target_host_name>', port '50000', dbname 'bludb')"`

   For example:<br/>
   `db2 "create server db2server type dashdb version 11 wrapper drda authorization \"admin2\" password \"YYYY\" options (host 'targetdotcom', port '50000', dbname 'bludb')"`

6. Create the user mapping for admin2:<br/>
   `db2 "create user mapping for <admin_user> server db2server options (remote_authid '<admin_user_on_target>', remote_password '<admin_password_on_target>')"`

   For example:<br/>
   `db2 "create user mapping for admin1 server db2server options (remote_authid 'admin2', remote_password 'YYYY')"`

7. Create a nickname for the database:<br/>
   `db2 -v "create nickname <nickname> for <server_name>.<schema_name>.<table_name>"`

   For example:<br/>
   `db2 -v "create nickname ntest1 for db2server.admin2.testdata"`

### On the Db2 on Cloud source machine

1. Test that you can pull data from the target server:<br/>
   `db2 "select * from <nickname>"`

   For example:<br/>
   `db2 "select * from ntest1"`
-->

### On a Db2 on Cloud machine being used as a federation source
{: #fed_src}

From the {{site.data.keyword.Db2_on_Cloud_short}} console:

1. Create a server to talk to the target machine:<br/>
   `create server <server_name> type dashdb version 11 wrapper drda authorization "<admin_user_on_target>" password "<admin_password_on_target>" options (host '<target_host_name>', port '50000', dbname 'bludb')`

   For example:<br/>
   `create server db2server type dashdb version 11 wrapper drda authorization "admin2" password "YYYY" options (host 'targetdotcom', port '50000', dbname 'bludb')`

2. Create the user mapping for admin2:<br/>
   `create user mapping for user server db2server options (remote_authid '<admin_user_on_target>', remote_password '<admin_password_on_target>')`

   For example:<br/>
   `create user mapping for user server db2server options (remote_authid 'admin2', remote_password 'YYYY')`

3. Create a nickname for the database:<br/>
   `create nickname <nickname> for <server_name>.<schema_name>.<table_name>`

   For example:<br/>
   `create nickname ntest1 for db2server.admin2.testdata`

4. Test that you can pull data from the target server:<br/>
   `select * from <nickname>`

   For example:<br/>
   `select * from ntest1`

## Additional information
{: #more_info}

For more information about data virtualization (federation), see: [Federation](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/fcontainer.html){:external}.

By default, {{site.data.keyword.Db2_on_Cloud_short}} supports Informix and Db2 (including on-premises Db2 and Db2 Warehouse). Support for certain data sources might need to be installed by IBM Support upon request. For information about the data sources supported by federation, see: [Federation Supported Data Sources](https://www.ibm.com/support/docview.wss?uid=swg27050561){:external}.

