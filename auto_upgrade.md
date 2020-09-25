---

copyright:
  years: 2014, 2020
lastupdated: "2020-09-25"

keywords: upgrade, Db2 on Cloud, Standard plan, Enterprise plan, legacy, automatic

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
{:support: data-reuse='support'}
{:faq: data-hd-content-type='faq'}
{:video: .video}

# Automatic upgrading and transitioning
{: #auto_upgrade_plans}

It is recommended that you complete the plan upgrade to the new {{site.data.keyword.Db2_on_Cloud_long}} Standard or Enterprise plan within the requested timeline. In most cases, the upgrade reduces your monthly costs and you are able to take advantage of improved features that are only available under the new plans. [What happens if I don't initiate the upgrade before the deadline?](/docs/Db2onCloud?topic=Db2onCloud-upgrade_plans#q_consequences){: external}. 
{: shortdesc}

In any case, immediately start the upgrade process by creating a new system from the [{{site.data.keyword.cloud_notm}} Catalog](https://cloud.ibm.com/catalog/services/db2){: external} and mapping your legacy plan CRN. For instructions, see [Upgrading Db2 on Cloud plans](/docs/Db2onCloud?topic=Db2onCloud-upgrade_plans){: external}. By upgrading now, you'll avoid the first deadline of **October 15, 2020** and remain in control of scheduling any testing and the transition before **November 1, 2020**. Self-initiating the upgrade process also ensures that you avoid system-availability downtime and the additional recovery steps that are required if your system is automatically upgraded.

## Deadline to self-initiate upgrade
{: #auto_ug_deadline}

The deadline to self-initiate the upgrade through the {{site.data.keyword.cloud_notm}} Catalog is **October 15, 2020, 8 PM ET**. The option to self-initiate the upgrade will not be available beyond this date. Make sure that you initiate the upgrade before the deadline. Starting on **October 16, 2020**, any {{site.data.keyword.Db2_on_Cloud_short}} legacy plan instances for which the upgrade was not initiated will be automatically upgraded.  

## Auto-upgrade process
{: #auto_ug_process}

The auto-upgrade process is initiated on the back end by the {{site.data.keyword.Db2_on_Cloud_short}} team. This auto upgrade is an online process similar to the self-initiated upgrade process that is currently available. If your instance is undergoing the auto-upgrade process, you can still continue to use the source legacy instance. For more information about this phase, see [Upgrade features and recommendations](/docs/Db2onCloud?topic=Db2onCloud-upgrade_plans#ug_feat_recom){: external}.

## Deadline to initiate transition
{: #auto_ug_trans_deadline}

The deadline to initiate the transition to the new plan instance applies only if you self-initiated the upgrade on or before **October 15, 2020**. The deadline to self-initiate the transition from the legacy instance is **November 1, 2020, 8 PM ET**. The option to self-initiate the transition will not be available beyond the November 1, 2020 date, so make sure to do so before the deadline. Any {{site.data.keyword.Db2_on_Cloud_short}} legacy plan instances for which the transition was not self-initiated before the deadline will be automatically transitioned starting on **November 2, 2020**.

## Auto-transition process
{: #auto_ug_trans_process}

The auto-transition process applies to legacy plan instances that underwent a self-initiated upgrade by **October 15, 2020**, but were not transitioned by **November 1, 2020**. In addition, auto transitioning also applies to legacy instances that were auto upgraded. All such legacy systems will be transitioned automatically. **Access to the legacy instance will be blocked immediately after transition.**

If you self-initiated the upgrade, start using your upgraded instance before **November 2, 2020** because all legacy systems will be blocked at this time. If your legacy plan instance was auto upgraded and access to the legacy system was blocked, you must generate a new set of credentials from the VCAP on your existing legacy plan instance on {{site.data.keyword.cloud_notm}} to retrieve the new hostname and port.

## Recovery
{: #auto_ug_recovery}

The recovery option applies only to legacy systems that were auto upgraded. At this point, the legacy instance belongs to the upgraded plan; however the legacy instance is still linked to the legacy resource on {{site.data.keyword.cloud_notm}}. To link the upgraded instance to the correct resource on {{site.data.keyword.cloud_notm}}, a recovery option will be provided through the {{site.data.keyword.cloud_notm}} Catalog starting on **November 2, 2020** after auto transitions begin. **Access to your system will not be available until the recovery steps are completed.**

More information about this option will soon be available.

