---

copyright:
  years: 2014, 2019
lastupdated: "2019-12-03"

keywords: Lite, plan, Lite plan, free plan, availability, restrictions, installation

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

# Free Lite plan
{: #free_plan}

The {{site.data.keyword.Db2_on_Cloud_long}} Lite plan provides basic resources for you to develop or learn about Db2 without charge.
{: shortdesc}

There is no time limit on the Lite plan, but users must re-extend their Lite plan every 30 days.

Only community support is available. 
 
## Architecture
{: #fp_architecture}

Unlike other {{site.data.keyword.Db2_on_Cloud_short}} plans, the free {{site.data.keyword.Db2_on_Cloud_short}} Lite plan runs on a multi-tenant system. The Flex and Precise Performance plans run on their own single-tenant virtual machines or bare metal servers.
 
The Lite plan uses one database schema.

For more information about the free {{site.data.keyword.Db2_on_Cloud_short}} Lite plan, see the [FAQ](https://ibm.biz/db2oc_free_plan_faq){:external}.

<!-- ## Using the Lite plan outside continental North America
{: #outside_na}

The Lite plan is accessible without a credit card for continental North America. Outside of continental North America, customers must add a credit card to their IBM Cloud account and then select the "US South - Dallas" region for the Lite plan to be visible for selection.

The Lite plan is always free and your credit card will not be charged.
-->

## Regional availability
{: #fp_availability}

The Lite plan is available in the Dallas and London regions. If you do not see the Lite plan listed in the catalog, select either Dallas or London region.

## Restrictions
{: #fp_restrictions}

It is recommended that you use an enterprise-level service plan rather than a Lite service plan for mission-critical or performance-sensitive workloads. 
{: important}

The following table contains {{site.data.keyword.Db2_on_Cloud_short}} Lite plan restrictions:

| Category | Item | Restriction | 
|----------|------|-------------|
| Resources | Storage | 200 MB of storage per user |
|  | Connections | 5 connections per user |
|  | Performance | Performance might fluctuate due to workloads run by other users on the multi-tenant system |
|  |  |
| Features & functions | Federation | Not supported |
|  | Oracle compatibility | Not supported |
|  | User-defined extensions (UDFs) | Not supported on any {{site.data.keyword.Db2_on_Cloud_short}} plans, including the Lite plan |
|  | User management | User not given administrative authority |
|  | Row and column access control (RCAC) | Not supported |
|  | IBM InfoSphere Data Replication for use in loading data | Not supported |
|  |  |
| Networking environment | IBM Cloud Integrated Analytics | Not supported |
|  | IBM Cloud Dedicated | Not supported |
|  |  |
| Security compliances | Health Information Portability and Accountability Act of 1996 (HIPAA) | Not supported. Refer to your Service Description. |
|  | EU General Data Protection Regulation (GDPR) | Not supported. Refer to your Service Description. |
|  |  |
| Account management | Reactivation | Reactivation required every 30 days. If not reactivated, Lite plan services are deleted 60 days later.  |
{: caption="Table 1. {{site.data.keyword.Db2_on_Cloud_short}} Lite plan restrictions" caption-side="top"}

## Installation
{: #fp_installation}

Watch this video to see how easy it is to install the free {{site.data.keyword.Db2_on_Cloud_short}} Lite plan.

<!-- <iframe class="embed-responsive-item" id="youtubeplayer1" title="Installation of the free {{site.data.keyword.Db2_on_Cloud_short}} Lite plan" type="text/html" width="640" height="390" src="//www.youtube.com/embed/YuMRRnl1bkE?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe> -->

![Installation of the free {{site.data.keyword.Db2_on_Cloud_short}} Lite plan](https://www.youtube.com/embed/YuMRRnl1bkE?rel=0){: video output="iframe" data-script="none" id="youtubeplayer1" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen}

