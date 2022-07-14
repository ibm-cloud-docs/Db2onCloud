---

copyright:
  years: 2021, 2022
lastupdated: "2022-06-23"

keywords: monitoring for code engine, performance metrics, monitor, metrics, requests, pods, application, attributes, jobrun, panic mode

subcollection: Db2onCloud

---

{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{:note .note}
{:note: .note}
{:objectc data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:terraform: .ph data-hd-interface='terraform'}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}


# Monitoring for {{site.data.keyword.Db2_on_Cloud_short}}
{: #monitor}

Get insight into your {{site.data.keyword.Db2_on_Cloud_short}} instance. These metrics can help you find bottlenecks or predict possible production problems.

You can use the IBM Cloud® Monitoring service to monitor your {{site.data.keyword.Db2_on_Cloud_short}} instance. {{site.data.keyword.Db2_on_Cloud_short}} forwards selected information about your instance to Monitoring so that you can monitor specific metrics such as cpu and memory utilization.

Monitoring metrics are currently available for only Enterprise and Standard plans. Lite plans are currently not supported.
{: important}

## Set up your {{site.data.keyword.Db2_on_Cloud_short}} service instance
{: #setup-monitor}

To set up Monitoring for {{site.data.keyword.Db2_on_Cloud_short}}, you must create a service instance and then enable Platform Metrics in the same region as the {{site.data.keyword.Db2_on_Cloud_short}} instance  that you want to monitor. If you have deployments in more than one region, you must provision Monitoring and enable platform metrics for each region.

To set up {{site.data.keyword.mon_short}},

1. From the {{site.data.keyword.cloud_notm}} navigation menu, select **Observability**.
2. Select **Monitoring**.
3. Either use an existing {{site.data.keyword.mon_short}} service instance or create a new one.
4. After the instance is ready, enable platform metrics by clicking **Configure platform metrics**.
5. Select a region and then a {{site.data.keyword.mon_short}} instance from that region. If you have deployments in more than one region, you must provision {{site.data.keyword.mon_short}} and enable platform metrics for each region.

## Accessing your {{site.data.keyword.mon_full_notm}} metrics
{: #access-monitor}

To see your {{site.data.keyword.Db2_on_Cloud_short}} customer metrics dashboards in {{site.data.keyword.mon_short}}:

1. From the {{site.data.keyword.cloud_notm}} navigation menu, select **Observability**.
2. Select **Monitoring**.
3. Select **View {{site.data.keyword.mon_full_notm}}** to open the dashboard.

For more information, see [{{site.data.keyword.mon_short}} Getting started tutorial](/docs/monitoring?topic=monitoring-getting-started).

## Metrics available by Service Plan
{: metrics-by-plan}
​
| Metric Name |
|-----------|
| [Database Availability Check](#ibm_db2_db_availability_check) | 
| [Database commits time](#ibm_db2_db_commits_time) | 
| [Database rollbacks](#ibm_db2_db_rollbacks) | 
| [Disaster recovery Log Gap](#ibm_db2_dr_log_gap) | 
| [High Availability Disaster Recovery Log Gap](#ibm_db2_hadr_log_gap) | 
| [Is disaster recovery connected?](#ibm_db2_is_dr_connected) | 
| [Last backup duration in minutes](#ibm_db2_last_backup_duration_minutes) | 
| [Log Disk wait](#ibm_db2_log_disk_wait) | 
| [Number of Unique ID statements](#ibm_db2_uid_stmts) | 
| [Number of rows deleted](#ibm_db2_rows_deleted) | 
| [Number of rows updated](#ibm_db2_rows_updated) | 
| [Numbers of rows inserted](#ibm_db2_rows_inserted) | 
| [Time since last backup in hours](#ibm_db2_since_last_backup_hours) | 
| [Total Activities Aborted](#ibm_db2_db_act_aborted) | 
| [Total Activities Completed](#ibm_db2_db_act_completed) | 
| [Total Activities Rejected](#ibm_db2_db_act_rejected) | 
| [Total Connections](#ibm_db2_total_conn) | 
| [Total number of commits](#ibm_db2_db_num_commits) | 


​
### Database Availability Check
{: #ibm_db2_db_availability_check}
​
​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_db_availability_check`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `The current status of the database.` |
{: caption="Table 1. Database availability check metric" caption-side="top"}


​
### Database commits time
{: #ibm_db2_db_commits_time}
​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_db_commits_time`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `Indicates the number of applications that are currently connected to the database.` |
{: caption="Table 2. Database commits time metric" caption-side="top"}

​
### Database rollbacks
{: #ibm_db2_db_rollbacks}
​​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_db_rollbacks`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `Total number of rollback statements issued by the client application and total number of rollbacks initiated internally by the database manager.` |
{: caption="Table 3. Database rollback metric" caption-side="top"}

​
### Disaster recovery Log Gap
{: #ibm_db2_dr_log_gap}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_dr_log_gap`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `Disaster Recovery Log Gap​.` |
{: caption="Table 4. Disaster recovery Log Gap metric" caption-side="top"}

​
### High Availability Disaster Recovery Log Gap
{: #ibm_db2_hadr_log_gap}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_hadr_log_gap`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `HADR Log Gap monitor element This element shows the recent average of the gap between the PRIMARY_LOG_POS value and STANDBY_LOG_POS value. The gap is measured in number ofbytes.` |
{: caption="Table 5. High Availability disaster recovery log gap metric" caption-side="top"}

​
### Is disaster recovery connected?
{: #ibm_db2_is_dr_connected}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_is_dr_connected`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `Availability disaster recovery connection status of the database.` |
{: caption="Table 6. Disaster recovery status metric" caption-side="top"}

​
### Last backup duration in minutes
{: #ibm_db2_last_backup_duration_minutes}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_last_backup_duration_minutes`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `The duration of the last successful backup.` |
{: caption="Table 7. Last backup time mteric" caption-side="top"}

​
### Log Disk wait
{: #ibm_db2_log_disk_wait}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_log_disk_wait`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `The number of times agents have to wait for log data to write to disk.` |
{: caption="Table 8. Log Disk wait metric" caption-side="top"}

​
### Number of Unique ID statements
{: #ibm_db2_uid_stmts}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_uid_stmts`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `The number of UPDATE, INSERT, MERGE and DELETE statements that were executed.` |
{: caption="Table 9. Number of unique ID statements metric" caption-side="top"}

​
### Number of rows deleted
{: #ibm_db2_rows_deleted}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_rows_deleted`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `Total of number of row deletions attempted and total number of rows deleted from the database as a result of internal activity.` |
{: caption="Table 10. Number of rows deleted metric" caption-side="top"}

​
### Number of rows updated
{: #ibm_db2_rows_updated}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_rows_updated`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `Total number of row updates attempted and total number of rows updated from the database as a result of internal activity.` |
{: caption="Table 11. Number of rows updated metric" caption-side="top"}

​
### Numbers of rows inserted
{: #ibm_db2_rows_inserted}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_rows_inserted`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `Total number of row insertions attempted and total number of rows inserted  from the database as a result of internal activity.` |
{: caption="Table 12. Number of rows inserted metric" caption-side="top"}

​
### Time since last backup in hours
{: #ibm_db2_since_last_backup_hours}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_since_last_backup_hours`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `The number of hours since there was a last successful backup.` |
{: caption="Table 13. Time since last backup in hours metric" caption-side="top"}

​
### Total Activities Aborted
{: #ibm_db2_db_act_aborted}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_db_act_aborted`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `The total number of coordinator activities at any nesting level that completed with errors.` |
{: caption="Table 14. Total activities aborted metric" caption-side="top"}

​
### Total Activities Completed
{: #ibm_db2_db_act_completed}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_db_act_completed`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `The total number of coordinator activities at any nesting level that completed successfully.` |
{: caption="Table 15. Total activities completed metric" caption-side="top"}

​
### Total Activities Rejected
{: #ibm_db2_db_act_rejected}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_db_act_rejected`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `The total number of coordinator activities at any nesting level that were rejected instead of being allowed to execute.` |
{: caption="Table 16. Total activities rejected metric" caption-side="top"}

​
### Total Connections
{: #ibm_db2_total_conn}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_total_conn`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance`, `Resource` |
| `Metric Description` | `Indicates the number of applications that are currently connected to the database.` |
{: caption="Table 17. Total connections metric" caption-side="top"}

​
### Total number of commits
{: #ibm_db2_db_num_commits}

​
| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_db2_db_num_commits`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` , `Resource` |
| `Metric Description` | `Total number of commit statements issued by the client application and the total number of commits initiated internally by the database manager.` |
{: caption="Table 18. Total number of commits metric" caption-side="top"}

​
## Attributes for Segmentation
{: attributes}
​
### Global Attributes
{: global-attributes}
​
The following attributes are available for segmenting all of the metrics listed above
​
| Attribute | Attribute Name | Attribute Description |
|-----------|----------------|-----------------------|
| `Cloud Type` | `ibm_ctype` | The cloud type is a value of public, dedicated or local |
| `Location` | `ibm_location` | The location of the monitored resource - this may be a region, data center or global |
| `Resource` | `ibm_resource` | The database member resource being measured by the service |
| `Scope` | `ibm_scope` | The scope is the account, organization or space GUID associated with this metric |
| `Service name` | `ibm_service_name` | Name of the service generating this metric |
​
### Additional Attributes
{: additional-attributes}
​
The following attributes are available for segmenting one or more attributes as described in the reference above.  Please see the individual metrics for segmentation options.
​
| Attribute | Attribute Name | Attribute Description |
|-----------|----------------|-----------------------|
| `Service instance` | `ibm_service_instance` | The service instance segment identifies the instance the metric is associated with |
