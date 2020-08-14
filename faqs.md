---

copyright:
  years: 2014, 2020
lastupdated: "2020-02-10"

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
{:support: data-reuse='support'}
{:faq: data-hd-content-type='faq'}
{:video: .video}

# FAQs
{: #faq_db2oc}

This is a collection of frequently asked questions (FAQ) about the {{site.data.keyword.Db2_on_Cloud_long}} service.
{: shortdesc}

## How do I sign up for Db2 on Cloud?
{: #q_sign}
{: faq}
{: support}

You can provision an instance of {{site.data.keyword.Db2_on_Cloud_short}} directly through the {{site.data.keyword.cloud}} catalog. You can [create a free {{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/registration?target=%2Fcatalog%2Fservices%2Fdb2-warehouse){: external} and get an {{site.data.keyword.cloud_notm}} credit of $200 that you can use towards an enterprise {{site.data.keyword.Db2_on_Cloud_short}} plan. Or, you can sign up for a free Lite plan. 

Watch the following video that walks you through provisioning a free Lite instance of {{site.data.keyword.Db2_on_Cloud_short}}.

![Introducing {{site.data.keyword.Db2_on_Cloud_long}}](https://www.youtube.com/embed/F_ylk44_WOg?rel=0){: video output="iframe" data-script="none" id="youtubeplayer1" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen}

## How do I choose the Db2 on Cloud plan that's right for me?
{: #q_choose_plan}
{: faq}
{: support}

{{site.data.keyword.Db2_on_Cloud_short}} offers several configurations to meet your workload requirements. The Flex plan is recommended because it allows you to dynamically scale RAM/CPU and storage as your requirements change. Other plans with fixed resources are also available. For more information, see [About](/docs/Db2onCloud?topic=Db2onCloud-about).

## How do I generate credentials for my instance?
{: #q_creds}
{: faq}
{: support}

1. Log into [IBM Cloud](https://cloud.ibm.com){: external}.
2. Open your [**Resource list**](https://cloud.ibm.com/resources){: external}.
3. Under **Services** or **Cloud Foundry services**, locate your {{site.data.keyword.Db2_on_Cloud_short}} instance and click on the service name.  
   - Services - This list includes all instances that were created under a resource group or that were migrated into a resource group.
   - Cloud Foundry services - This list includes all instances that were created under a Cloud Foundry organization and space, and were not migrated into a resource group.
4. Select the **Service credentials tab > New credentials+ > Add** in order to generate your service admin credentials.
5. Expand **View credentials**, which displays your service connectivity information including your admin credentials (username and password).
6. The admin credentials can be used to connect to both Db2 and the web console.


## Now that I've generated credentials, how do I access my Db2 on Cloud instance?
{: #q_access}
{: faq}
{: support}

You can access your {{site.data.keyword.Db2_on_Cloud_short}} instance through several methods, including a dedicated web console and a REST API. For more information, see [Interfaces](/docs/Db2onCloud?topic=Db2onCloud-interfaces).

## What's managed for me with Db2 on Cloud?
{: #q_managed}
{: faq}
{: support}

IBM handles all of the software upgrades, operating system updates, and hardware maintenance for your {{site.data.keyword.Db2_on_Cloud_short}} instance. IBM also preconfigures Db2 parameters for optimal performance across transactional workloads, and takes care of encryption and regular backups of your data. 

The service includes 24x7 health monitoring of the database and infrastructure. In the event of a hardware or software failure, the service is automatically restarted. Because {{site.data.keyword.Db2_on_Cloud_short}} is a fully-managed SaaS offering, you do not get SSH access or root access to the underlying server hardware, and cannot install additional software.

## Where can I find more information about Db2 on Cloud?
{: #q_info}
{: faq}
{: support}

In addition to the {{site.data.keyword.cloud_notm}} documentation site, there is a wide range of information about the underlying Db2 engine functionality in the [Knowledge Center](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.kc.doc/welcome.html){: external}. Updates to the service are posted on our [What's New](https://www.ibm.com/support/pages/whats-new-ibm-db2-cloud){: external} page. 

You can find pricing information and deploy a {{site.data.keyword.Db2_on_Cloud_short}} instance through the {{site.data.keyword.cloud_notm}} [catalog](https://cloud.ibm.com/catalog/services/db2){: external} page for {{site.data.keyword.cloud_notm}}. To learn more, contact [IBM Sales](https://www.ibm.com/contact/us/en/){: external}.


## Where can I find help for a problem that I'm having?
{: #q_issues}
{: faq}
{: support}

For information about posting questions on a forum or opening a support ticket, see [Help & support](/docs/Db2onCloud?topic=Db2onCloud-help_support).

Only community support is available for the free Lite plan.


