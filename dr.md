---

copyright:
  years: 2014, 2020
lastupdated: "2020-10-08"

keywords: DR, HADR, disaster recovery, legacy, Flex, Db2 on Cloud, failover

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

# Geo-Replicated Disaster Recovery (DR)
{: #dr_gen}

<!-- High availability disaster recovery (HADR) provides a high availability solution for both partial and complete site failures. HADR protects against data loss by replicating data changes from a source database, called the primary database, to the target databases, called the standby databases.
{: shortdesc} -->

Db2 on Cloud leverages Db2’s HADR technology and lets users add a DR Node, on demand, in an offsite data center of their choice. In an unlikely event where the primary data server is affected by external circumstances such as a natural disaster, users can failover to their Geo-Replicated Disaster Recovery Node with a few clicks. Users can also fail back to their primary site just as easily.

## High Availability vs. Disaster Recovery
Db2 on Cloud's High Availability Plan offers Db2's HADR SYNC and ASYNC nodes technology to deliver superior availability and reliability, within the same region. When required, failover to the HA nodes is managed seamlessly and automatically by IBM using automatic client reroute (ACR).  HA plans reside within a single MZRs or SZR region

With the introduction of Geo-Replicated Disaster Recovery Nodes, customers are now able to extend that availability to an entirely different region by adding an on-demand Disaster Recovery Node.  This ensures that users can still access their data in the unlikely event of an outage in their primary region. (e.g., Primary Instance: Dallas, DR Node: London).


## Enterprise and Standard HADR Plans

DR nodes are now available for Enterprise and Standard HADR plans only. DR nodes are currently not supported in Single Node plans or in Eu-Cloud.  

### Creating a DR node

1. Select the **Administration** button from the menu on the left and then the **Disaster Recovery** tab on the top.
   ![View of the Disaster Recovery Page](images/dr_1_v2.jpg  "Console opens to DR Page"){: caption="Figure 1. View of the DR page" caption-side="bottom"}

2. Select a datacenter for the DR node adn click on the **Enable Disaster Recovery** button
   ![Select a DR DataCenter](images/dr_2_v2.jpg  "Select a datacener for the DR node"){: caption="Figure 2. Select a DataCenter for the Recovery node" caption-side="bottom"}

3. The new DR node is displayd on the Disaster Recovery screen along with a notification indicating a sucessful deployment.
   ![DR Deployed](images/dr_3_v2.jpg  "Recovery Node created"){: caption="Figure 3. Recovery node sucessfully created" caption-side="bottom"}

### Forcing a failover to the DR Site

1. To force a failover to the DR site, open the Console on the Recovery node from the IBMCloud dashboard or by clicking the blue **Promote** button on the primary node console
   ![Recovery Node Console](images/dr_4_v2.jpg  "Recovery Node Console"){: caption="Figure 1. Recovery node console" caption-side="bottom"}

2. Click on the blue **Promote** button on the Recovery node console to initiate a takeover
      ![Recovery Node Takeover](images/dr_5_v2.jpg  "Recovery Node Takeover"){: caption="Figure 2. Recovery node takeover" caption-side="bottom"}

3. Click on the blue **Promote** button on the takeover confirmation screen
      ![Takeover Confirmation](images/dr_6_v2.jpg  "Takeover Confirmation"){: caption="Figure 3. Recovery node takeover" caption-side="bottom"}

4. Takeover can take up to 30 minutes depending on the size of the database.
      ![Takeover Progress](images/dr_7_v2.jpg  "Takeover Progress"){: caption="Figure 4. Takeover Progress Bar" caption-side="bottom"}

5. A sucessfuly takeover on the recovery node is indicated by the blue **Promotion** button moving to the primary node, along with a notification. The Recovery node is now **Active**
   ![Takeover Completion](images/dr_8_v2.jpg  "Takeover Completion"){: caption="Figure 5. Takeover Completion" caption-side="bottom"}

### Forcing a Failback to Primary Site

1.  To force a failover back to the primary site, open the Console on the primary node (which is now the the standby) from the IBMCloud dashboard or by clicking the blue **Promote** button on the Recovery node console
   ![Primary Node Console](images/dr_9_v2.jpg  "Primary Node Console"){: caption="Figure 1. Primary node console" caption-side="bottom"}

2. Click on the blue **Promote** button on the Primary node console to initiate a takeover.  The takeover confirmation screen appears.  Click on the blue **Promote** button on the takeover confirmation screen to initiate the takeover
      ![Primary Node Takeover](images/dr_10_v2.jpg  "Primary Node Takeover"){: caption="Figure 2. Priamry node takeover" caption-side="bottom"}

3. Takeover can take up to 30 minutes depending on the size of the database.
      ![Takeover Progress](images/dr_11_v2.jpg  "Takeover Progress"){: caption="Figure 4. Takeover Progress Bar" caption-side="bottom"}

4. A sucessfuly takeover on the recovery node is indicated by the blue **Promotion** button moving to the primary node, along with a notification.   The primary site is now **Active**
   ![Takeover Completion](images/dr_12_v2.jpg  "Takeover Completion"){: caption="Figure 5. Takeover Completion" caption-side="bottom"}

5. 

<!--## Legacy Flex plans
{: #dr_legacy}

{{site.data.keyword.Db2_on_Cloud_short}} Legacy Flex plans feature disaster recovery (DR) capabilities, where users can add a DR node, which resides in a different region, by using the Db2 High Availability Disaster Recovery (HADR) technology. Promoting to the recovery site gives users the ability to recover data affected by unpredictable circumstances. The Recovery site is always in a different region than the Primary site.

In the case of a disaster, the failover to the recovery site will not be initiated by IBM. For the DR failover, you must initiate the takeover from the UI. In the case of a failure in the primary site, it is important to remember that you will not have access to the primary system to initiate the takeover. 

Bookmark the **Manage Disaster Recovery** page found under the **Manage** menu item in your {{site.data.keyword.Bluemix_notm}} dashboard.
{: important}

To enable the DR failover, complete the following steps:

1. Select **Manage Disaster Recovery** under the **Manage** menu item in your {{site.data.keyword.Bluemix_notm}} dashboard.
   ![View of the Manage dashboard page](images/dr_step1.png "Dashboard opens to the Manage page"){: caption="Figure 1. View of the Manage dashboard page" caption-side="bottom"}
2. Click **Access Recovery Site Console**.
   ![View of the Manage Disaster Recovery page](images/dr_step2.png "Dashboard opens to the Manage Disaster Recovery page"){: caption="Figure 2. View of the Manage Disaster Recovery page" caption-side="bottom"}
3. Log in with your `bluadmin` credentials.
   ![View of the DR login page](images/dr_step3.png "DR login"){: caption="Figure 3. View of the DR login page" caption-side="bottom"}
4. Click **Initiate Takeover on Recovery Site** to initiate the takeover on the recovery site.
   ![View of the DR takeover page](images/dr_step4.png "Initiate DR takeover"){: caption="Figure 4. View of the DR takeover page" caption-side="bottom"}
5. In the case of the primary site connect status being `Disconnected`, you'll have to navigate to the recovery site URL, which is found in the file that was downloaded by clicking on the **Download Disaster Recovery Details** link on the **Manage Disaster Recovery** page. Log in with your credentials and issue a failover.

## Standard and Enterprise plans
{: #dr_stan_ent}

HADR is available. See [How is the high availability disaster recovery (HADR) feature done in Standard and Enterprise plans?](/docs/Db2onCloud?topic=Db2onCloud-upgrade_plans#q_dr){: external}.

-->


