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

# Auditing
{: #auditing}

You can monitor data access in your {{site.data.keyword.Db2_on_Cloud_long}} instance with the built-in Db2 audit facility. Use the Db2 audit facility to generate and maintain an audit trail for a series of predefined database events, including attempts to access or manipulate database objects, user authentication, SQL statement execution, and even access to the audit log. Use the audit log to reveal usage patterns that would identify system misuse, and in turn, take action to eliminate such misuse.
{: shortdesc}

For more information about auditing for {{site.data.keyword.Db2_on_Cloud_short}}, see [Audit policy guidelines](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.security.doc/doc/audit_policy_guidelines.html){: external}.


You can also audit and track changes to your database by using the following method:
* By creating a `CHANGE HISTORY` event monitor, you can query the event monitor table to determine what was done within the database and by whom. For more information, see [`CHANGE HISTORY` event monitor](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:external}.
<!-- * The Time Travel Query gives you the ability to store all of the changes to your data and even query your old data based on a selected point in time. To use this audit method, ensure that you first set up your tables to support Time Travel Query. For more information, see: [Time Travel Query](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:external} -->

For more information about auditing and tracking database changes, see: [How do I audit or track changes?](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:external}.



