---

copyright:
  years: 2014, 2020
lastupdated: "2020-11-11"

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

# Differences between legacy and current plans
{: #plan_diffs}

There are many differences between legacy plans and the new Standard and Enterprise plans, as described across the product documentation. This topic describes the key changes you'll need to make in your applications when you upgrade to a Standard or Enterprise plan.
{: shortdesc}

## Connectivity
{: #wn_connectivity}

1. The hostname of the Standard and Enterprise plan is different.

2. The port number changes from port 50000 to a unique port number.

3. Connections to the database default to SSL.

4. Console and REST API hostname is different from JDBC URL. 

For more information, see [Connectivity options](/docs/Db2onCloud?topic=Db2onCloud-connect_options){: external}.

## Credentials
{: #wn_creds}

1. New credentials must be created in {{site.data.keyword.cloud_notm}} to access the database instance. 

2. Credentials on {{site.data.keyword.cloud_notm}} do not include `bluadmin`, but the user still exists to connect to the database.

For more information about creating credentials, see [Connectivity options](/docs/Db2onCloud?topic=Db2onCloud-connect_options){: external}.

## VCAP
{: #wn_vcap}

The current Standard and Enterprise plans **VCAP Services** json file is different from that of the legacy plans. Any of your applications that consume the legacy plan **VCAP Services** json file must be changed to handle the current Standard and Enterprise plans json file. 

For more information about the Standard and Enterprise **VCAP Services** json file, see [Connectivity options](/docs/Db2onCloud?topic=Db2onCloud-connect_options){: external}.

## Console
{: #wn_console}

Console user-management differences (including IAM-only access to certain features).

For more information about user management and roles, see [Managing users](/docs/Db2onCloud?topic=Db2onCloud-user_mgmt){: external}.

## Db2
{: #wn_db2}

Standard and Enterprise plans do not run with the `DB2_WORKLOAD=ANALYTICS` registry parameter, hence the behavior of the COUNT aggregate function has changed. COUNT now returns an **INTEGER**, not a DECIMAL value. 

For more information, see [COUNT aggregate function](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.sql.ref.doc/doc/r0000759.html){: external}.

