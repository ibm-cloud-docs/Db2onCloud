---

copyright:
  years: 2014, 2021
lastupdated: "2021-03-17"

keywords: DR, HADR, disaster recovery, Enterprise, Standard, Db2 on Cloud, failover, failback

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
{:video: .video}

# Geo-replicated disaster recovery (DR)
{: #dr_gen}

{{site.data.keyword.Db2_on_Cloud_short}} leverages Db2 HADR technology and gives you the ability to add a DR node, on demand, in an offsite data center of your choice. In an unlikely event that the primary data server is affected by external circumstances such as a natural disaster, you can failover to your Geo-Replicated Disaster Recovery node with a few clicks. You can also fail back to your primary site just as easily.
{: shortdesc}

Admin functionality is not available on the DR node. Any admin functions must be run on the primary instance while it's **Active**.
{: important}

DR nodes are currently set up to adopt the KMS instance and disk encrption key of the primary data server in the case that the primary data server uses Hyper Protect Crypto Services for encryption.
{: important}

DR nodes are currently available for only Enterprise and Standard HADR plans. DR nodes are currently not supported in single node plans or in EU-Cloud.
{: important}

Failover to the DR site is not automatic. You must initiate the failover.
{: important}

Deleting a DR configuration is currently not supported on the {{site.data.keyword.cloud_notm}} dashboard. To delete the DR configuration, you must open a support ticket. Deleting a DR configuration removes both the primary and DR sites.
{: important}
 
[Creating a DR node](#dr_create_dr_node)

[Forcing a failover to the DR site](#dr_force_failover)

[Forcing a failback to the primary site](#dr_force_failback)

<!--High availability disaster recovery (HADR) provides a high availability solution for both partial and complete site failures. HADR protects against data loss by replicating data changes from a source database, called the primary database, to the target databases, called the standby databases.
-->

## High Availability vs. Disaster Recovery
{: #dr_ha_vs_dr}

{{site.data.keyword.Db2_on_Cloud_short}} High Availability plan offers Db2 HADR SYNC and ASYNC nodes technology to deliver superior availability and reliability, within the same region. When required, failover to the HA nodes is managed seamlessly and automatically by IBM using automatic client reroute (ACR). HA plans reside within a single MZR or SZR region.

With the introduction of Geo-Replicated Disaster Recovery nodes, you are now able to extend that availability to an entirely different region by adding an on-demand Disaster Recovery node. This ability ensures that you can still access your data in the unlikely event of an outage in your primary region. For example, primary instance: Dallas; DR node: London.

## Enterprise and Standard HADR plans
{: #dr_ent_std_plans}

DR nodes are now available for Enterprise and Standard HADR plans only. DR nodes are currently not supported in single node plans or in EU-Cloud.  

### Creating a DR node
{: #dr_create_dr_node}

1. Select **Administration** from the left menu, then select the **Disaster recovery** tab.
   ![View of the Disaster Recovery page](images/dr_1_v2.jpg  "Console opens to DR Page"){: caption="Figure 1. View of the DR page" caption-side="bottom"}

2. Select a data center for the DR node and click **Enable disaster recovery**.
   ![Select a DR data center](images/dr_2_v2.jpg  "Select a data center for the DR node"){: caption="Figure 2. Select a data center for the recovery node" caption-side="bottom"}

3. The new DR node is displayed on the **Disaster recovery** page along with a notification indicating a successful deployment.
   ![DR Deployed](images/dr_3_v2.jpg  "Recovery node created"){: caption="Figure 3. Recovery node sucessfully created" caption-side="bottom"}

### Forcing a failover to the DR site
{: #dr_force_failover}

1. To force a failover to the DR site, open the web console for the recovery site from the {{site.data.keyword.cloud_notm}} dashboard. 
   ![Recovery node console](images/dr_4_v2.jpg  "Recovery node console"){: caption="Figure 4. Recovery node console" caption-side="bottom"}

2. To initiate a takeover, click **Promote** on the **Disaster recovery** page.
   ![Recovery node takeover](images/dr_5_v2.jpg  "Recovery node takeover"){: caption="Figure 5. Recovery node takeover" caption-side="bottom"}

3. Click **Promote** to confirm takeover.
   ![Takeover confirmation](images/dr_6_v2.jpg  "Takeover confirmation"){: caption="Figure 6. Takeover confirmation" caption-side="bottom"}

4. Takeover can take up to 30 minutes, depending on the size of the database.
   ![Takeover progress](images/dr_7_v2.jpg  "Takeover progress"){: caption="Figure 7. Takeover progress bar" caption-side="bottom"}

5. A successful takeover by the recovery node is indicated by the **Promotion** button moving to the primary node (now the standby) along with a notification. The recovery site is now **Active**.
   ![Takeover completion](images/dr_8_v2.jpg  "Takeover completion"){: caption="Figure 8. Takeover completion" caption-side="bottom"}

### Forcing a failback to the primary site
{: #dr_force_failback}

1. To force a failback to the primary site, open the web console for the primary site from the {{site.data.keyword.cloud_notm}} dashboard.
   ![Primary node console](images/dr_9_v2.jpg  "Primary node console"){: caption="Figure 9. Primary node console" caption-side="bottom"}

2. To initiate a takeover, click **Promote** on the **Disaster recovery** page. The takeover confirmation screen appears. Click **Promote** on the takeover confirmation screen to initiate the takeover.
   ![Primary node takeover](images/dr_10_v2.jpg  "Primary node takeover"){: caption="Figure 10. Priamry node takeover" caption-side="bottom"}

3. The takeover can take up to 30 minutes, depending on the size of the database.
   ![Takeover progress](images/dr_11_v2.jpg  "Takeover progress"){: caption="Figure 11. Takeover progress bar" caption-side="bottom"}

4. A successful takeover by the primary node is indicated by the **Promotion** button moving to the recovery node (now the standby) along with a notification. The primary site is now **Active**.
   ![Takeover completion](images/dr_12_v2.jpg  "Takeover completion"){: caption="Figure 12. Takeover completion" caption-side="bottom"}

<!--
## Legacy Flex plans
{: #dr_legacy}

{{site.data.keyword.Db2_on_Cloud_short}} Legacy Flex plans feature disaster recovery (DR) capabilities, where users can add a DR node, which resides in a different region, by using the Db2 High Availability Disaster Recovery (HADR) technology. Promoting to the recovery site gives users the ability to recover data affected by unpredictable circumstances. The Recovery site is always in a different region than the Primary site.

In the case of a disaster, the failover to the recovery site will not be initiated by IBM. For the DR failover, you must initiate the takeover from the UI. In the case of a failure in the primary site, it is important to remember that you will not have access to the primary system to initiate the takeover. 

Bookmark the **Manage Disaster Recovery** page found under the **Manage** menu item in your {{site.data.keyword.Bluemix_notm}} dashboard.
{: important}

To enable the DR failover, complete the following steps:

1. Select **Manage Disaster Recovery** under the **Manage** menu item in your {{site.data.keyword.Bluemix_notm}} dashboard.
   ![View of the Manage dashboard page](images/dr_step1.png "Dashboard opens to the Manage page"){: caption="Figure 1. View of the Manage dashboard page" caption-side="bottom"}
1. Click **Access Recovery Site Console**.
   ![View of the Manage Disaster Recovery page](images/dr_step2.png "Dashboard opens to the Manage Disaster Recovery page"){: caption="Figure 2. View of the Manage Disaster Recovery page" caption-side="bottom"}
1. Log in with your `bluadmin` credentials.
   ![View of the DR login page](images/dr_step3.png "DR login"){: caption="Figure 3. View of the DR login page" caption-side="bottom"}
1. Click **Initiate Takeover on Recovery Site** to initiate the takeover on the recovery site.
   ![View of the DR takeover page](images/dr_step4.png "Initiate DR takeover"){: caption="Figure 4. View of the DR takeover page" caption-side="bottom"}
1. In the case of the primary site connect status being `Disconnected`, you'll have to navigate to the recovery site URL, which is found in the file that was downloaded by clicking on the **Download Disaster Recovery Details** link on the **Manage Disaster Recovery** page. Log in with your credentials and issue a failover.

## Standard and Enterprise plans
{: #dr_stan_ent}

HADR is available. See [How is the high availability disaster recovery (HADR) feature done in Standard and Enterprise plans?](/docs/Db2onCloud?topic=Db2onCloud-upgrade_plans#q_dr){: external}.

-->


