---

copyright:
  years: 2014, 2020
lastupdated: "2020-03-04"

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

# Logging and monitoring
{: #log_mon}

Monitoring and logging is part of the service. However, it is not directly displayed to the user. Instead, the infrastructure is used by IBM operational staff to address issues.  

<!-- For availability of the Activity Tracker, see [roadmap](https://ibm.biz/db2oncloud-roadmap){:external}. -->

You can connect with a Db2 command-line client, such as CLPPlus, to access detailed information and diagnostics.

## A basic overview:
{: #basic_overview}

The following are two basic types of checking your system status:
- External health and uptime checks 
- Metric-based monitoring 

IBM monitors hundreds of metrics and stores those metrics historically. Based on the values of these metrics, alerts are generated. These alerts are sent to IBM operations staff to ensure that the alerts are seen and addressed. In addition, IBM also sends archived operating system and diagnostic logs for rapid diagnosis. {{site.data.keyword.Db2_on_Cloud_short}} complies with GDPR, and IBM EU Cloud options provide an even higher level of adherence to GDPR, if needed.


