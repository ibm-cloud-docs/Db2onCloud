---

copyright:
  years: 2014, 2021
lastupdated: "2021-03-11"

keywords: self-serve, system update, plan

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

# Self-serve system updates
{: #self_serve_update}

Many updates on your {{site.data.keyword.Db2_on_Cloud_short}} Enterprise, Standard or DR instance are offered as self-serve updates, which means you have the ability to apply system updates to your instances at a time of your choosing. No email notifications are sent for this type of update. You'll be notified through your console. There might be a time limit within which you must apply the update, typically 30 days, before it is automatically applied to your instance.

However, some updates impact all of the users sharing a common infrastructure, or are required immediately to keep your system secure. You can't schedule these updates. Additional details about these types of updates are coming soon.

The update process can be disruptive, especially for single node instances, so it's advisable to run the update during a maintenance window.
{: important}

## Enterprise and Standard plan Updates
{: #ssu_plans}

<!--
Enterprise and Standard plans give you the ability to apply system updates to your instances at a time of your choosing. -->

### Notification
{: #ssu_notif}

For self-serve updates, you are notified of an instance system update through the **Notifications** icon in the upper right of the console. 

![Update notification](images/ss_notification.png "Self-serve update notification"){: caption="Figure 1. Self-serve update notification" caption-side="bottom"}

Clicking **View details** brings up the **System update** information window that displays the new Db2 version of {{site.data.keyword.Db2_on_Cloud_short}}.  

![System update](images/ss_system_update.png "System update information"){: caption="Figure 2. System update information" caption-side="bottom"}

### Updating
{: #ssu_updating}

You can click **Update now** to initiate the update when you're ready. 

With the update initiated, a progress window is presented under the **Notifications** icon.

![Update Progress](images/ss_progress.png "System Update Progress"){: caption="Figure 3. System Update Progress" caption-side="bottom"}

### Update completion
{: #ssu_fin}

Upon completion of a successful update, a **Success!** window appears.

![Successful](images/ss_success.png "Successful update"){: caption="Figure 4. Successful Update" caption-side="bottom"}



## DR Plan Updates

Updates to DR instance must always be applied the **Recovery site** first, while it's in **Standby** mode, before applying to the **Primary site** in **Active** mode {: important}

### Notification
{: #ssu_notif}

For self-serve updates, you are notified of an instance system update through the **Notifications** icon in the upper right of the console on both the **Primary** and **Recovery** sites. 

### Update the Recovery Site First
The Console on the **Recovery** site will display a system update through the **Notifications** icon on the upper right.  The screenshot below shows the console is for the Recovery site in London and is in **Standy** mode

![Recovery version update Info](images/ssu_dr_recovery_info.jpg "Recovery ersion update info"){: caption="Figure 1. Recovery site version update info" caption-side="bottom"}

Clicking **View details** brings up the **System update** information window that displays the new Db2 version of {{site.data.keyword.Db2_on_Cloud_short}}.  


### Updating
{: #ssu_updating}

You can click **Update now** to initiate the update when you're ready. 

With the update initiated, a progress window is presented under the **Notifications** icon.

![System update](images/ssu_dr_recovery_update.jpg "System update information"){: caption="Figure 2. Recovery site system update information" caption-side="bottom"}

### Update completion
{: #ssu_fin}

Upon completion of a successful update, a **Success!** window appears.

![Successful](images/ssu_dr_recovery_success.jpg "Successful update"){: caption="Figure 3. Recovery site successful update" caption-side="bottom"}

### Update the Primary Site After Updating the Recovery Site
The Console on the **Primary** site will display a system update through the **Notifications** icon on the upper right.  

The Primary site must only be update when it's **Active** and after the **Recovery** site has been updated first.{: important}

The screenshot below shows the console is for the **Primary** site in Dallas and is in **Active** mode

![Primary version update Info](images/ssu_dr_primary_info.jpg "Primary version update info"){: caption="Figure 1. Primary Site version update info" caption-side="bottom"}

Clicking **View details** brings up the **System update** information window that displays the new Db2 version of {{site.data.keyword.Db2_on_Cloud_short}}. 

### Updating
{: #ssu_updating}

You can click **Update now** to initiate the update when you're ready. 

With the update initiated, a progress window is presented under the **Notifications** icon.

![System update](images/ssu_dr_primary_update.jpg "System update information"){: caption="Figure 2. Primary site system update information" caption-side="bottom"}

### Update completion
{: #ssu_fin}

Upon completion of a successful update, a **Success!** window appears.

![Successful](images/ssu_dr_primary_success.jpg "Successful update"){: caption="Figure 3. Primary site successful update" caption-side="bottom"}