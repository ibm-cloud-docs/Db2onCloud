---

copyright:
  years: 2014, 2020
lastupdated: "2020-09-15"

keywords: upgrade, Db2 on Cloud, Standard plan, Enterprise plan, legacy

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

# Upgrading {{site.data.keyword.Db2_on_Cloud_short}} plans
{: #upgrade_plans}

The following document describes the process to upgrade from the legacy {{site.data.keyword.Db2_on_Cloud_short}} plans to the current **Standard** and **Enterprise** plans. Henceforth, the existing legacy plan instance is referred to as the "source" and the newly provisioned Standard or Enterprise plan instance for the upgrade is referred to as the "target".
{: shortdesc}

For more information about the affected legacy plans and the new replacement plans, see [Deprecation of the Db2 on Cloud Legacy Plans and Availability of New Replacement Plans](https://www.ibm.com/cloud/blog/announcements/deprecation-of-the-db2-on-cloud-legacy-plans-and-availability-of-new-replacement-plans){: external}.

You can also refer to the [What's New in IBM Db2 on Cloud](https://www.ibm.com/support/pages/node/739537){: external} where the new plans and features were announced. 

The legacy plan upgrade is currently available in the following data centers:
- Dallas
- Frankfurt
- London
- Sydney
- Tokyo
- Washington

The legacy plan upgrade will be available in the following data centers before or by **September 30, 2020**:
- Amsterdam
- Milan
- Paris
- Toronto

For those of you with a **HIPAA** requirement, the new systems are targeted to be ready by **September 30,2020**. 

Legacy-style disaster recovery (DR) is planned to be supported by **November 30, 2020**. However, [read more](#q_leverage_ha) about the high-availability nodes spanning multiple zones now available with the new plans to determine if this satisfies your DR requirements.

## Prerequisites
{: #upgrade_prereqs}

Before starting the legacy plan upgrade process, you'll need to complete the following items:
- Retrieve the Cloud Resource Name (CRN) of your source {{site.data.keyword.Db2_on_Cloud_short}} plan. The CRN can be retrieved from the source plan on {{site.data.keyword.cloud_notm}}. For more information, see [Cloud Resource Names](/docs/account?topic=account-crn).
- If your source plan is still in Cloud Foundry, you must migrate your source plan to Resource Controller. See [Resource controller (RC)](/docs/Db2onCloud?topic=Db2onCloud-rc). After you migrate a plan instance to Resource Controller, you can no longer use Cloud Foundry CLI commands to manage it.

  Additional information:
  - [Managing resource groups](/docs/account?topic=account-rgs#adding-resources-to-a-resource-group)
  - [General {{site.data.keyword.cloud_notm}} CLI (ibmcloud) commands](/docs/cli?topic=cli-ibmcloud_cli)

## Ordering from the {{site.data.keyword.cloud_notm}} Catalog
{: #ug_catalog}

1. Log in to the {{site.data.keyword.cloud_notm}} account where the existing source {{site.data.keyword.Db2_on_Cloud_short}} plan was provisioned.
1. Navigate to the [{{site.data.keyword.Db2_on_Cloud_short}} catalog page](https://cloud.ibm.com/catalog/services/db2){: external}
1. Choose the **Enterprise** or **Standard** plan and input the CRN of the source {{site.data.keyword.Db2_on_Cloud_short}} plan. The {{site.data.keyword.Db2_on_Cloud_short}} Lite plan is not eligible for the upgrade. The source plan must belong to one of the following legacy plans: 
   - Flex
   - Precise Performance 500
   - Precise Performance 1400 
   
## Tracking the upgrade
{: #ug_track}

- Navigate to the source plan on the {{site.data.keyword.cloud_notm}} dashboard
- Track the status of the upgrade by clicking on the **Upgrade** button

## Upgrade phases
{: #ug_phases}

The upgrade from the legacy {{site.data.keyword.Db2_on_Cloud_short}} plans to the current **Standard** and **Enterprise** plans is a self-service and online process. It is initiated the moment a target plan is ordered along with a source CRN input. The upgrade goes through multiple phases and for a majority of them no user action is required.

### Phase 0 - Provisioning target
{: #ug_prov_tgt}

The target plan is provisioned and scaled automatically to the appropriate level. The values used for scale depend on the current configuration of the source. No user action is required for this phase.

### Phase 1 - Preparing upgrade
{: #ug_prep}

The prerequisite steps required to upgrade the source to the target plan are run during this phase. No user action is required for this phase.

### Phase 2 - Metadata migration
{: #ug_meta_mig}

The metadata such as DDL and the database user information existing on the source are migrated to the target during this phase. No user action is required for this phase.

### Phase 3 - Data migration
{: #ug_data_mig}

The data from the source is migrated to the target. No user action is required for this phase.

### Phase 4 - Data migration complete
{: #ug_data_mig_cmplt}

User action is required for this phase.
{: important}

The data has been migrated from the source to the target. Any transactions on the source continue to be replicated on the target, but it is possible to transition to the target. After the upgrade reaches this phase, a **Transition** button is now available on the source plan on {{site.data.keyword.cloud_notm}} where the upgrade is tracked. In order to proceed to the next phase, user action is required to initiate the transition.

### Phase 5 - Transition in progress
{: #ug_trans_inprog}

Certain post-migration tasks are run on the target during this phase. No user action is required for this phase.

### Phase 6 - Transition and upgrade complete
{: #ug_trans_inprog_cmplt}

The upgrade is complete. The target plan is now available to use. Any further transactions on the source will NOT be replicated on the target.

## Upgrade features and recommendations
{: #ug_feat_recom}

- The upgrade process is a self-service and online process
- Users can continue to use their source plan while the upgrade proceeds
- Every upgrade is monitored by the {{site.data.keyword.Db2_on_Cloud_short}} Operations team who are available 24x7x365
- The data replication is unidirectional - from the source to the target
- Any users created or modified on the source DURING or AFTER the upgrade process might not be migrated to the target. It is recommended that no user administration actions are performed after the upgrade is initiated.
- Any DDL changes on the source DURING or AFTER the upgrade process might not be replicated on the target. It is recommended that no DDL changes are attempted on the source after the upgrade is initiated.
- It is recommended that users do not insert, update or delete any data on the target during the upgrade. Any read operation is possible and can be used to verify the data migration
- Users can continue using the source until transition is initiated. The average transition period is about two minutes. In case the transition has not completed even after 30 minutes, you are recommended to continue using the source. The {{site.data.keyword.Db2_on_Cloud_short}} Operations team will be alerted if there is an issue with the transition and will re-enable the button when it is possible to transition again.

## Billing during the upgrade
{: #ug_billing}

- You are NOT billed for the target during the upgrade. You will be billed for the source as usual.
- If you do not initiate transition after a period of 2 weeks since the option was available, you will be billed for the target
- After the upgrade is complete, you will be billed for the target and will NOT be billed for the source
- If you do not delete the source plan prior to the end of the 2 week grace period following completion of the upgrade, you will then be billed for the source again

## FAQs - Upgrading to Standard and Enterprise plans
{: #faq_db2oc_upgrade}

This is a collection of frequently asked questions (FAQ) about upgrading the {{site.data.keyword.Db2_on_Cloud_long}} plans. We'll add more questions over time. [Create a case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external} if you have any questions about the upgrade and migration.
{: shortdesc}

Email notifications are being sent to customers associated with existing {{site.data.keyword.Db2_on_Cloud_short}} legacy plan instances. If you have not been receiving email notifications, ensure that account email addresses for {{site.data.keyword.Db2_on_Cloud_short}} plans are up to date. Many of you received an email alerting you to our new Standard and Enterprise plans, and the need for you to upgrade your legacy plans to our new plans via our online upgrade process, because we are deprecating support for our legacy plans. Upgrades will start in **August**. You have until **October 15, 2020** to initiate your upgrade and until **October 30, 2020** to complete testing and connect to your new system. Access to legacy systems will not be available after **November 1, 2020** and these systems will be decommissioned during November.
{: important}

### How long will the upgrade take from Phase 0 to Phase 4 (Transition Ready)?
{: #q_upgrade_duration}
{: faq}
{: support}

The upgrade of each of your plans and databases is unique and depends on many factors, which might result in different time frames between creating the new system to being notified that the transition is available. The time required can range between 6 hours and a multiple of days.

The upgrade process is a completely online process and requires a time period of hours or days to complete. There are various factors that govern the pace of the upgrade. Some of the factors are the amount of data on the source, storage capacity on the target, the type and relationship between the data, the compute configurations of the source and target, the physical location and distance between the source and target, networking considerations such as the presence of allowlists or private endpoints, data-center-specific latency, the volume of workload on the source during the upgrade, to name a few. There are also other factors to take into consideration. Due to the presence of such a large and varied number of factors, it is not possible to provide an accurate time estimate for the upgrade. The time taken by the upgrade will not impact your use of the source on which there will be zero downtime during the upgrade.

### What's new in our Standard and Enterprise plans?
{: #q_wn}
{: faq}
{: support}

Our new Standard and Enterprise plans run the Db2 11.5 engine. They include self-scheduling of software updates by customers, zero down-time scaling of storage and compute, self-service managed backup with point-in-time restore, and support for several {{site.data.keyword.cloud_notm}} integration features like **Activity Tracker** and **LogDNA**. If you choose a high-availability (HA) option, you get three high-availability nodes spanning multiple availability zones (where supported).

<!--
### What are the plan specs?
{: #q_plan_specs}
{: faq}
{: support}

- **Enterprise**: You get one SQL database per service instance on dedicated compute slices with 4 vCPUs, 16 GB of RAM, and 20 GB of storage for data and logs. Each plan includes up to 1 TB of backup storage, stored for 14 days.

- **Standard**: You get one SQL database per service instance on a shared compute environment with 8 GB of RAM, and 20 GB of storage for data and logs. Each plan includes up to 100 GB of backup storage, stored for 14 days.

With either plan, you can scale up by purchasing additional storage or CPU. You can also purchase additional backup storage, Cloud Service Endpoint connectivity or HA options.
-->

### How much do the Standard and Enterprise plans cost?
{: #q_cost}
{: faq}
{: support}

Prices are detailed by plan in the [{{site.data.keyword.cloud_notm}} catalog](https://cloud.ibm.com/catalog/services/db2){: external}

### Will I be billed for two plans during the upgrade?
{: #q_bill_two}
{: faq}
{: support}

After you begin the upgrade, you have 14 days to move to the new plan. The upgrade timeline starts when you provision a {{site.data.keyword.Db2_on_Cloud_short}} Standard or Enterprise plan and provide your CRN from your legacy plan in the upgrade details on the **Service create** page in the {{site.data.keyword.cloud_notm}} catalog. If you don't complete the upgrade during that 14 day period, you will be charged for both source and target plans.

### Can I leverage the new HA feature in the new plans in place of our existing DR node solution in the legacy plans? 
{: #q_leverage_ha}
{: faq}
{: support}

The new plans offer a High Availability (HA) feature with 3 nodes located in different independent availability zones and the failover is managed for you by IBM. This feature avoids any service disruption caused by a data center disaster, failure, or maintenance. HA is also well suited as a disaster recovery (DR) option for those of you with requirements that are satisfied by it. If you have strict requirements for a cross-region DR node, you can leverage such a feature by **November 30, 2020**.

### I have a non-HA plan, but want to upgrade to HA (or vice versa). Can I do that?
{: #q_noha_ha}
{: faq}
{: support}

Yes, you can move from any legacy plan (Flex, Small, and Large) to any {{site.data.keyword.Db2_on_Cloud_short}} Standard and Enterprise plan. You can move from non-HA to HA, or from HA to non-HA. If you have a DR node, be aware there are changes to DR in Standard and Enterprise plans. See the following question about DR changes in Standard and Enterprise plans.

### How is disaster recovery (DR) changing in Standard and Enterprise plans?
{: #q_dr}
{: faq}
{: support}

Standard and Enterprise plans provide automated redundancy across 3 different data centers with the HA options. These data centers are physically isolated from each other and do not share any infrastructure. The reference design for different data centers within an MZR is that they are separated by at least 10 km or 6 mi. This is a significant improvement from our legacy plans in which you can have only 2 nodes which are in a single data center. In addition, Standard and Enterprise HA plans also provide `Read on standby` capability. {{site.data.keyword.Db2_on_Cloud_short}} also provides backups, which can be restored to a completely new region should all data centers be unrecoverable. These backups, as well as archive logs, are geo-replicated across several regions (more than 400 km or 250 mi away from the MZR), protecting you from even the worst natural disasters. In many cases, this will suffice instead of having a DR node in a different region. If not, we do intend to provide a DR option and timelines are being finalized.

### My plan instance is still on Cloud Foundry. Do I need to migrate it to Resource Controller before I upgrade to a Standard or Enterprise plan?
{: #q_rc}
{: faq}
{: support}

Yes, you'll need to migrate to Resource Controller. See [Resource controller (RC)](/docs/Db2onCloud?topic=Db2onCloud-rc).

After you migrate a plan instance to Resource Controller, you can no longer use Cloud Foundry CLI commands to manage it.

Additional information:
- [Managing resource groups](/docs/account?topic=account-rgs#adding-resources-to-a-resource-group)
- [General {{site.data.keyword.cloud_notm}} CLI (ibmcloud) commands](/docs/cli?topic=cli-ibmcloud_cli)

### What permissions will I need to initiate the upgrade to a Standard or Enterprise plan?
{: #q_perms}
{: faq}
{: support}

You must be a platform admin user on both source and target plan instances.

### What will I need to change after the upgrade to a new plan?
{: #q_change}
{: faq}
{: support}

We'll move your data, DDL, and all of your database users. All that you must do is update your applications to use a new hostname and port.

<!--
### What is the V2 upgrade timeline?
{: #q_timeline}
{: faq}
{: support}

We will send out notifications starting in **early August**. As we finish the prerequisites needed for your specific instance(s), we'll notify you that we are ready. You have until **October 15, 2020** to complete the upgrade, which means you should plan to start by early October at the latest.
-->

### What happens if I don't initiate the upgrade before the deadline?
{: #q_consequences}
{: faq}
{: support}

If you don't initiate the upgrade from your {{site.data.keyword.Db2_on_Cloud_short}} legacy plan by **October 15, 2020**, we will start the upgrade on your behalf by creating a new {{site.data.keyword.Db2_on_Cloud_short}} plan instance, moving your data, DDL, and users into your new plan. Your legacy plan instance will remain in your dashboard list of resources and you will continue to be billed for this legacy plan instance, but, under the covers, your instance will be a Standard or Enterprise plan. It is strongly recommended that you complete the plan upgrade to the new {{site.data.keyword.Db2_on_Cloud_short}} Standard or Enterprise plan. In most cases, the upgrade will lower your monthly costs.

<!--More details about how you can connect to your auto-upgraded plan and how you will be billed will be provided in the near future.-->

<!-- If you don't initiate the upgrade, we will block access to your {{site.data.keyword.Db2_on_Cloud_short}} V1 system on **October 1, 2020**. You can reinstate access by creating a new V2 service instance or contacting our support team. If by **October 15**, you do nothing, we will start the migration on your behalf by creating a {{site.data.keyword.Db2_on_Cloud_short}} V2 system, move your data, DDL, and users into our new V2 plans, but without touching your V1 service instance. In other words, you'll still see your V1 plan in your list of service instances, and will continue to be billed for this V1 service instance, but under the covers your instance will be in a V2 plan. It is strongly recommended that you complete the upgrade so that your service instance is updated to the {{site.data.keyword.Db2_on_Cloud_short}} V2 plan. In most cases, this will lower your monthly costs. If you maintain both the V1 and V2 systems, you will be billed for both systems after the 14 day grace period. -->

<!--
### What do I need to do if my system was automatically upgraded?
{: #q_auto_upgrade}
{: faq}
{: support}

If you didn't initiate the upgrade and we created a V2 system on your behalf, you will lose connectivity to your V1 instance on **November 2, 2020** when we transition any remaining systems from V1 to V2. To gain access to your new system, log in to your cloud dashboard to obtain new access credentials and host information for your V2 system.  Update any {{site.data.keyword.Db2_on_Cloud_short}} applications with the new connection information. You completed the upgrade process. You upgraded your V1 plan to the new V2 plan with its related pricing. You can now delete the V1 plan.
-->

### You told me that I have an upgraded plan instance, but I can't find it in the {{site.data.keyword.cloud_notm}} dashboard -- what do I do?
{: #q_find}
{: faq}
{: support}

<!--You might not have access to the service instance if you have only been connecting to it directly without going through {{site.data.keyword.cloud_notm}}. You probably provisioned it under a different account. Maybe you received an email because you own a functional ID that owns one or more instances.--> 
If you are having difficulty, [create a case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external}.

### I decided not to move my data to the new Standard or Enterprise plan. What should I do to opt out?
{: #q_opt_out}
{: faq}
{: support}

You must delete your legacy plan instance from the {{site.data.keyword.cloud_notm}} dashboard or contact Customer Support. We are moving all plans to the new Standard and Enterprise plans because of the upcoming **End of Support** of a key component in our legacy plans. <!-- For this reason we have no exception process for retaining your V1 legacy instance beyond November. If you have a business reason for needing an additional week or two after the **October 15, 2020** deadline, we will consider the request. The reason that we give a deadline of October 15 is because on this day we will start initiating the upgrade for all remaining instances (i.e. for any instance where the owner did not initiate it themselves). -->

### What if I previously created a new Standard or Enterprise plan instance and I want to migrate to it?
{: #q_previous_v2}
{: faq}
{: support}

You cannot migrate to an existing Standard or Enterprise plan instance after it's been previously created. You must delete your existing Standard or Enterprise plan instance and follow the steps outlined here to initiate the upgrade to a target to which you can migrate.

### What if I'm not receiving emails related to this legacy plan upgrade?
{: #q_no_emails}
{: faq}
{: support}

The owner of your {{site.data.keyword.cloud_notm}} account that is associated with the legacy {{site.data.keyword.Db2_on_Cloud_short}} plan instance must [create a case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external} to add additional email addresses to the {{site.data.keyword.cloud_notm}} account.

### How can I learn more?
{: #q_learn_more}
{: faq}
{: support}

- For additional information about the plan upgrades, see [Upgrading {{site.data.keyword.Db2_on_Cloud_short}} plans](#upgrade_plans).
- For information about our Standard and Enterprise plans, see [About: Plans and configurations](/docs/Db2onCloud?topic=Db2onCloud-about#ab_plans_cfgs)
- [Blog post announcing new Enterprise HA plan](https://www.ibm.com/cloud/blog/announcements/db2-on-cloud-announces-new-enterprise-high-availability-plan){: external}
- [Blog post announcing new Standard HA plan](https://www.ibm.com/cloud/blog/announcements/db2-on-cloud-standard-plan){: external}
- [What's New](https://www.ibm.com/support/pages/node/739537){: external} about the {{site.data.keyword.Db2_on_Cloud_short}} Standard and Enterprise plans now available in 6 data centers, including support for Oracle compatibility




