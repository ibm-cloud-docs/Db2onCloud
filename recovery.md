---

copyright:
  years: 2014, 2021
lastupdated: "2021-02-25"

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

# Recovery steps after auto upgrade
{: #recovery}

If you did not start the upgrade process from your legacy plan or there were technical issues with the self-initiated upgrade, you will be automatically upgraded in a rolling fashion starting **November 11, 2020**. The following instructions describe the workflow to recover an auto-upgraded system.
{: shortdesc}

<!--
These steps can be run on an instance only after the initiation of the auto-upgrade by the {{site.data.keyword.Db2_on_Cloud_short}} team. If your legacy instance is still online and available, then the auto-upgrade was not initiated and you must not run the following recovery procedure steps.
{: important}
-->

## Recovery procedure
{: #rec_steps}

1. [Log in to the {{site.data.keyword.cloud_notm}} account](http://cloud.ibm.com){: external} where the legacy {{site.data.keyword.Db2_on_Cloud_short}} system was provisioned.

   ![List of instances](images/recovery_instance_list_blur.png "List of instances"){: caption="Figure 1. Highlight your service instance" caption-side="bottom"}

2. Retrieve the CRN of your legacy instance. <!-- now listed under **Services**.-->

   ![Retrieve the legacy plan CRN](images/recovery_CRN_blur.png "Retrieve the legacy plan CRN"){: caption="Figure 2. Retrieve the legacy plan CRN" caption-side="bottom"}

3. Order a Standard or Enterprise instance. **Do not** enter any value in the Recovery field. Retrieve the CRN of your new instance.

   ![Initiate the recovery](images/recovery_v2.png "Initiate the recovery"){: caption="Figure 3. Initiate the recovery" caption-side="bottom"}

4. Open a support case and request the recovery of your instance. Be sure to provide the CRN of both your legacy instance and the new instance. The time to recover depends on the size of the database, but in most cases it is completed in less than 24 hours.

<!--1. The new {{site.data.keyword.Db2_on_Cloud_short}} service instance is visible under **Services**. However, the new instance is not ready for use until the owner of the account is notified by email that it is available for use.

1. The time to recovery depends on the size of the database, but in most cases it is completed in less than 24 hours.
-->

<!-- 2. If your legacy plan instance is listed under **Cloud Foundry services**, it must be migrated to a resource group. 

   ![Cloud Foundry instance](images/recovery_cf_blur.png "Cloud Foundry instance"){: caption="Figure 2. Cloud Foundry instance" caption-side="bottom"}

   - To migrate to a resource group, select the instance and click **Migrate**. After completion of the migration, the Db2 instance is now listed under **Services**.

     ![Cloud Foundry Migration](images/recovery_cf_migration_blur.png "Cloud Foundry Migration"){: caption="Figure 3. Migrating Cloud Foundry Instance" caption-side="bottom"}
-->
