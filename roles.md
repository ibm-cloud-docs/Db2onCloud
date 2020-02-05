---

copyright:
  years: 2014, 2020
lastupdated: "2020-02-04"

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

# User roles
{: #user_roles}

You can define user roles to manage data access at the user level on your {{site.data.keyword.Db2_on_Cloud_long}} instance. Users can be added to roles that reflect their job functions and you can enforce data access policies based on their respective roles.
{: shortdesc}

User roles can easily be implemented through a series of SQL statements. You can use the SQL editor of the web console. For example, you can create a role for your data science team by running the following SQL statement:

`CREATE ROLE DATASCIENCE`

Then, if you want to give your data scientists access to sales data, run the following statement:

`GRANT SELECT ON TABLE SALESDATA TO ROLE DATASCIENCE`

You can repeat the previous statement for all of the tables that you want your data science team to be able to access.

Next, add your data science team to the `DATASCIENCE` role. Assuming that you have two data scientists, Alice and Bob who exist as users of the database, you can then add them to the `DATASCIENCE` role by running the following SQL statement:

`GRANT ROLE DATASCIENCE TO USER ALICE, USER BOB`

Alice and Bob are now able to work on all of the data that is accessible to the `DATASCIENCE` role.

For more information about user roles in {{site.data.keyword.Db2_on_Cloud_short}}, see [User-defined user roles](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.security.doc/doc/udef_user_roles.html){: external}.

<!--
For a tutorial about how to implement user roles and Row and Column Access Control (RCAC) for your {{site.data.keyword.Db2_on_Cloud_short}} instance, see [RCAC](https://www.ibm.com/cloud/garage/dte/tutorial/row-and-column-access-control-rcac-ibm-db2-warehouse-cloud){: external}.
-->

