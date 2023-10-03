---

copyright:
  years: 2014, 2022
lastupdated: "2023-01-17"

keywords:

subcollection: Db2whc

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



# Auditing events for Db2 Warehouse on Cloud

{{site.data.keyword.at_full_notm}} allows you to forward the Db2 diagnostic log (db2diag.log) from your {{site.data.keyword.cloud_notm}} instances to your own Log Analysis with LogDNA service instance. Choosing to enable log forwarding allows you to use Log Analysis to retain these logs for the time period required by your organization, or to search or analyze the logs.

As a security officer, auditor, or manager, you can use the {{site.data.keyword.at_full}} service to track how users and applications interact with the Db2 Warehouse on Cloud service in {{site.data.keyword.cloud_notm}}. {: shortdesc}

{{site.data.keyword.at_full_notm}} records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. You can use this service to investigate abnormal activity and critical actions and to comply with regulatory audit requirements. In addition, you can be alerted about actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard. For more information, see the getting started tutorial for {{site.data.keyword.at_full_notm}}.

Activity Tracker with LogDNA integration is available for {{site.data.keyword.dashdblong}} deployments in the regions according to the following table: 

| Deployment region | Activity Tracker region |
|----------|-----------|
| Dallas | us-south |
| Washington | us-east |
| Frankfurt | eu-de |
| London | eu-gb |
| Sydney | au-syd |
| Tokyo | jp-tok |
| Toronto | ca-tor |
{: caption="Table 1. Activity Tracker regions" caption-side="top"}


## Activity Tracker with LogDNA provisioning
{: #at_log_analysis}

After you provision the service, events are automatically forwarded from all of your {{site.data.keyword.dashdblong}} deployments in the same region.

The service can be provisioned from its [catalog page](https://cloud.ibm.com/catalog/services/logdnaat?callback=%2Fobserve%2Factivitytracker%2Fcreate){: external} or from an existing [Observability Dashboard](https://cloud.ibm.com/observe/activitytracker){: external}.

The Activity Tracker with LogDNA service has a Lite plan that is free to use, but it only offers streaming events. To take advantage of the tagging, export, retention, and other features, you need to use one of the [paid plans](/docs/activity-tracker?topic=activity-tracker-service_plan).


## Event fields
{: #at_ev_fields}

A description of the common fields for an Activity Tracker event is on the [Event fields](/docs/activity-tracker?topic=activity-tracker-event) page.

## List of events
{: #at_list_ev}

The following table lists the events that get sent to Activity Tracker from {{site.data.keyword.dashdblong}} deployments:

| Action | Description |
|-------|-------|
| `<service_id>.backup-scheduled.create`| A scheduled backup of your deployment was created. If the backup failed, a "-failure" flag is included in the message. |
| `<service_id>.backup.create`| A backup of your deployment was created. If the backup failed, a "-failure" flag is included in the message. |
| `<service_id>.backup.restore`| A restore from backup was created. If the attempted restore failed, a "-failure" flag is included in the message. |
| `<service_id>.restore.start`| A restore from backup was created. If the attempted restore failed, a "-failure" flag is included in the message. |
| `<service_id>.user-password.update`| A user's password was updated. A "-failure" flag is included in the message if the attempt to update a user's password failed. |
| `<service_id>.user.create`| A user was created. A "-failure" flag is included in the message if the attempt to create a user failed. |
| `<service_id>.user.delete`| A user was deleted. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.table.delete`| A table was deleted. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.token.create`| A token was created. A "-failure" flag is included in the message if the attempt to create a user failed. |
| `<service_id>.token.delete`| A token was deleted. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.privilege.update`| A privilege was granted. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.privilege.revoke`| A privilege was revoked. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.database-connection.list`| Lists active database connections. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.database-connection.stop`| Terminates a database connection. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.lock.enable`| Locks a user account indefinitely. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.lock.disable`| Unlocks a user account. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.policy.list`| Lists available policies. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.policy.update`| A policy was updated. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.policy.delete`| A policy was deleted. "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.schema.create| A schema was created. A "-failure" flag is included in the message if the attempt to delete a user failed. |

The `<service_id>` field indicates the type of {{site.data.keyword.databases-for}} deployment. For example, `dashdb` or `messages-for-rabbitmq`.
## Viewing events
You can access Activity Tracker with LogDNA through the **Observability** tab of your deployment's **Manage** page. The **Manage Activity Tracker** button links to the main list of all Activity Tracker instances in your {{site.data.keyword.cloud_notm}} account. Select the instance where you set your database logs to be forwarded. {{site.data.keyword.at_full_notm}} can have only one instance per location. Click **View Activity Tracker** to view the events.

After the event activity is forwarded to the service, each event can be expanded to a detailed view by clicking the arrow to the left of the time stamp.

The Activity Tracker with LogDNA service offers [searching](/docs/log-analysis?topic=log-analysis-view_logs#view_logs_step6), [filtering](/docs/log-analysis?topic=log-analysis-view_logs#view_logs_step5), and [export](/docs/log-analysis?topic=log-analysis-export#export) of events so you can customize retention for your use case. You can also use it to configure [alerts](/docs/log-analysis?topic=log-analysis-alerts).
