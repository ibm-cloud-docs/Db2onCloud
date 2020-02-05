---

copyright:
  years: 2014, 2020
lastupdated: "2020-01-31"

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

# Auditing, logging, and monitoring
{: #aud-log-mon}

## Auditing
{: #auditing}

You can create a database audit policy that gives you the ability to audit various categories of events that are stored in audit event tables in your database. For more information, see [Audit policy guidelines](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.security.doc/doc/audit_policy_guidelines.html){:external}.

You can also audit and track changes to your database by using the following methods:
* By creating a `CHANGE HISTORY` event monitor, you can query the event monitor table to determine what was done within the database and by whom. For more information, see [`CHANGE HISTORY` event monitor](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:external}.
* The Time Travel Query makes it easy to store all of the changes to your data and even query your old data based on a selected point in time. To use this audit method, ensure that you first set up your tables to support Time Travel Query. For more information, see [Time Travel Query](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:external}

For more information about auditing and tracking database changes, see [How do I audit or track changes?](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:external}.

## Logging and monitoring
{: #log_mon}

Monitoring and logging is part of the service. However, it is not directly displayed to the user. Instead, the infrastructure is used by IBM operational staff to address issues.  

For availability of the Activity Tracker, see [roadmap](https://ibm.biz/db2oncloud-roadmap){:external}.

You can connect with a Db2 command-line client, such as CLPPlus, to access detailed information and diagnostics.

### A basic overview:
{: #basic_overview}

There are two basic types of checking. External health and uptime checks and metric-based monitoring. IBM monitors hundreds of metrics and stores those metrics historically. Based on the values of these metrics, alerts are generated. These alerts are sent to IBM operations staff to ensure that the alerts are seen and addressed. In addition, IBM also sends archived operating system and diagnostic logs for rapid diagnosis. {{site.data.keyword.Db2_on_Cloud_short}} complies with GDPR, and IBM EU Cloud options provide an even higher level of adherence to GDPR, if needed.


