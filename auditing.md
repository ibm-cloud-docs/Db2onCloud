---

copyright:
  years: 2014, 2023
lastupdated: "2023-07-21"

keywords: 

subcollection: Db2onCloud

---

 
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

As a security officer, auditor, or manager, you can use the {{site.data.keyword.at_full}} service to track how users and applications interact with the Db2 on Cloud service in {{site.data.keyword.cloud_notm}}. {: shortdesc}

{{site.data.keyword.at_full_notm}} records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. You can use this service to investigate abnormal activity and critical actions and to comply with regulatory audit requirements. In addition, you can be alerted about actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard. For more information, see the getting started tutorial for {{site.data.keyword.at_full_notm}}.

Activity Tracker with LogDNA integration is available for {{site.data.keyword.Db2_on_Cloud_long}}deployments in the regions according to the following table: 

| Deployment region | Activity Tracker region |
|----------|-----------|
| Dallas | us-south |
| Washington | us-east |
| Frankfurt | eu-de |
| London | eu-gb |
| Sydney | au-syd |
| Tokyo | jp-tok |
| São Paulo | br-sao |
| Toronto | ca-tor |
{: caption="Activity Tracker regions" caption-side="top"}


## Activity Tracker with LogDNA provisioning
{: #at_log_analysis}

After you provision the service, events are automatically forwarded from all of your {{site.data.keyword.Db2_on_Cloud_long}} deployments in the same region.

The service can be provisioned from its [catalog page](https://cloud.ibm.com/catalog/services/logdnaat?callback=%2Fobserve%2Factivitytracker%2Fcreate){: external} or from an existing [Observability Dashboard](https://cloud.ibm.com/observe/activitytracker){: external}.

The Activity Tracker with LogDNA service has a Lite plan that is free to use, but it only offers streaming events. To take advantage of the tagging, export, retention, and other features, you need to use one of the [paid plans](/docs/activity-tracker?topic=activity-tracker-service_plan).


## Event fields
{: #at_ev_fields}

A description of the common fields for an Activity Tracker event is on the [Event fields](/docs/activity-tracker?topic=activity-tracker-event) page.

## List of events
{: #at_list_ev}

The following table lists the events that get sent to Activity Tracker from {{site.data.keyword.Db2_on_Cloud_long}} deployments:

| Action | Description |
|-------|-------|
| `<service_id>.backup-scheduled.create`| A scheduled backup of your deployment was created. If the backup failed, a "-failure" flag is included in the message. |
| `<service_id>.backup.create`| A backup of your deployment was created. If the backup failed, a "-failure" flag is included in the message. |
| `<service_id>.backup.restore`| A restore from backup was created. If the attempted restore failed, a "-failure" flag is included in the message. |
| `<service_id>.restore.start`| A restore from backup was created. If the attempted restore failed, a "-failure" flag is included in the message. |
| `<service_id>.user-password.update`| A user's password was updated. A "-failure" flag is included in the message if the attempt to update a user's password failed. |
| `<service_id>.user.create`| A user was created. A "-failure" flag is included in the message if the attempt to create a user failed. |
| `<service_id>.user.delete`| A user was deleted. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.resources.scale`| A scaling operation was performed. If the scaling operation failed, a "-failure" flag is included in the message. |
| `<service_id>.privilege.update`| A privilege was granted of revoked. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.whitelisted-ips-list.update`| The allowlist was modified. A "-failure" flag is included in the message if the attempt to modify the allowlist failed. |
| `<service_id>.serviceendpoints.update`| A change has been made to the service endpoints configuration. If the operation failed, a "-failure" flag is included in the message. |
| `<service_id>.schema.create`| A schema was created. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.privilege.revoke`| A privilege was revoked. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.database-connection.list`| Lists active database connections. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.database-connection.stop`| Terminates a database connection. A "-failure" flag is included in the message if the attempt to delete a user failed. |

The `<service_id>` field indicates the type of {{site.data.keyword.databases-for}} deployment. For example, `db2` or `dashdb-for-transactions` or `messages-for-rabbitmq`.


## Viewing events
You can access Activity Tracker with LogDNA through the **Observability** tab of your deployment's **Manage** page. The **Manage Activity Tracker** button links to the main list of all Activity Tracker instances in your {{site.data.keyword.cloud_notm}} account. Select the instance where you set your database logs to be forwarded. {{site.data.keyword.at_full_notm}} can have only one instance per location. Click **View Activity Tracker** to view the events.

After the event activity is forwarded to the service, each event can be expanded to a detailed view by clicking the arrow to the left of the time stamp.

The Activity Tracker with LogDNA service offers [searching](/docs/log-analysis?topic=log-analysis-view_logs#view_logs_step6), [filtering](/docs/log-analysis?topic=log-analysis-view_logs#view_logs_step5), and [export](/docs/log-analysis?topic=log-analysis-export#export) of events so you can customize retention for your use case. You can also use it to configure [alerts](/docs/log-analysis?topic=log-analysis-alerts).

[Learn more about auditing](/docs/Db2onCloud?topic=Db2onCloud-auditing).

## Database Auditing
{: #database_auditing}

You can monitor data access in your {{site.data.keyword.Db2_on_Cloud_long}} instance with the built-in Db2 audit facility. Use the Db2 audit facility to generate and maintain an audit trail for a series of predefined database events, including attempts to access or manipulate database objects, user authentication, SQL statement execution, and even access to the audit log. Use the audit log to reveal usage patterns that would identify system misuse, and in turn, take action to eliminate such misuse.
{: shortdesc}

For more information about auditing for {{site.data.keyword.Db2_on_Cloud_short}}, see [Audit policy guidelines](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.security.doc/doc/audit_policy_guidelines.html){: external}.


You can also audit and track changes to your database by using the following method:
* By creating a `CHANGE HISTORY` event monitor, you can query the event monitor table to determine what was done within the database and by whom. For more information, see [`CHANGE HISTORY` event monitor](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){: external}.



Access to SYSCAT.AUDITPOLICIES, SYSIBMADM.PRIVILEGES, and SYSCAT.AUDITUSE will be revoked for PUBLIC. This only impacts clients who have explicitly assigned these privileges to PUBLIC. A client can choose to re-add the privileges to PUBLIC. {: important}


For more information about auditing and tracking database changes, see: [How do I audit or track changes?](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){: external}.
