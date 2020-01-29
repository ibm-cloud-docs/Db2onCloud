---

copyright:
  years: 2014, 2019
lastupdated: "2019-10-07"

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

# Resource controller (RC)
{: #rc}

The {{site.data.keyword.Db2_on_Cloud_long}} service now supports resource controller (RC). The RC is responsible for controlling and tracking the lifecycle of resources in an {{site.data.keyword.Bluemix_notm}} account. Resources is a broad term that can mean anything from an instance of a service like {{site.data.keyword.Db2_on_Cloud_short}}, a Cloud Foundry application, a virtual machine, a container, a software image, a data set, or other entity associated with an account.
{: shortdesc}

## Migrating Cloud Foundry services to RC
{: #mig_cf_rc}

Available with the resource controller is the ability to manage your service and app resources by using *resource groups*. For information about how and why you should migrate your Cloud Foundry service instances and apps to resource groups, see [Migrating Cloud Foundry service instances and apps to a resource group](/docs/resources?topic=resources-migrate).

To be able to use the new features such as [IBM Key Protect](/docs/Db2onCloud?topic=Db2onCloud-key-protect) and [Copy Database](/docs/Db2onCloud?topic=Db2onCloud-cp_db), you must migrate your Cloud Foundry service instances to RC.
{: important}

