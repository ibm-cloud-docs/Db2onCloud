---

copyright:
  years: 2014, 2021
lastupdated: "2021-01-19"

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

# About
{: #about}

{{site.data.keyword.Db2_on_Cloud_long}} is a fully managed public cloud service on {{site.data.keyword.cloud_notm}}. As a relational database, it delivers fast query processing with enterprise-level performance and capabilities for online transactional processing (OLTP). The new Enterprise High Availability plan runs the powerful Db2 11.5 engine, and also provides multizone region support in a three HA node configuration to ensure ultimate redundancy.
{: shortdesc}

## Key features
{: #ab_key_features}

### Scalable and elastic cloud service

{{site.data.keyword.Db2_on_Cloud_short}} is an elastic service, and allows you to independently scale compute and storage through an intuitive UI or REST API.

### Expertly managed and highly secure

Day-to-day operations for {{site.data.keyword.Db2_on_Cloud_short}}, including database monitoring, uptime checks and failovers, are fully automated. Operations are supplemented by a DevOps team that are on call to handle unexpected system failures. Data is encrypted at rest and in motion by default. Administrators can also restrict access to sensitive data through data masking, row permissions, and role-based security, and can utilize database audit utilities to maintain audit trails for their database. IBM Key Protect and {{site.data.keyword.cloud_notm}} service endpoint are also supported.

### Run your own apps

In addition to the integrated tools, you can connect many popular third-party BI and visualization apps that you might already be using. For example, connect IBM InfoSphere Data Architect to design and deploy your database schema, or connect SQL-based tools such as Watson Analytics and Cognos Analytics to manipulate or analyze your data. For the managed service, you can connect other {{site.data.keyword.cloud_notm}} applications.

### Graphical user interface or command line

You can use the web console to perform many key tasks, such as loading data, working with tables, run SQL, and monitoring. Alternatively, you can use the command-line user interface CLPPlus to define, edit, and run statements, scripts, and commands.

## Plans and configurations
{: #ab_plans_cfgs}

### Enterprise High Availability Disaster Recovery (HADR) plan

- Base instances start at 4 vCPU x 16 GB RAM x 20 GB storage on dedicated compute slices
- Runs the latest release of Db2, version 11.5
- Three HADR nodes spanning multiple availability zones
- 1 TB of free backup storage for up to 14 days of backups
- Self-service managed backup with point-in-time restore

### Enterprise non-High Availability Disaster Recovery (non-HADR) plan

- Base instances start at 4 vCPU x 16 GB RAM x 20 GB storage on dedicated compute slices
- Runs the latest release of Db2, version 11.5
- Single node in one availability zone
- 1 TB of free backup storage for up to 14 days of backups
- Self-service managed backup with point-in-time restore

### Standard High Availability Disaster Recovery (HADR) plan

- Base instances start at 8 GB RAM x 20 GB storage on shared compute slices
- Runs the latest release of Db2, version 11.5
- Three HADR nodes spanning multiple availability zones
- 100 GB of free backup storage for up to 14 days of backups
- Self-service managed backup with point-in-time restore

### Standard non-High Availability Disaster Recovery (non-HADR) plan

- Base instances start at 8 GB RAM x 20 GB storage on shared compute slices
- Runs the latest release of Db2, version 11.5
- Single node in one availability zone
- 100 GB of free backup storage for up to 14 days of backups
- Self-service managed backup with point-in-time restore

## Supported data centers
{: #ab_sup_dcs}

The Standard and Enterprise plans are supported in the following data center geographies:

### Multi-zone region (MZR) 
- **Dallas** - (Dal10, Dal12, Dal13)
- **Frankfurt** - (Fra02, Fra04, Fra05)
- **London** - (Lon04, Lon05, Lon06)
- **Sydney** - (Syd01, Syd04, Syd05)
- **Tokyo** - (Tok02, Tok04, Tok05)
- **Washington, DC** - (Wdc04, Wdc06, Wdc07)
- **Sao Paulo** - (Sao01, Sao04, Sao05)
- **Toronto** - (Tor01, Tor04, Tor05)

MZRs support 3 node HA in 3 different data centers in that region
{: note}

### Single-zone region (SZR)
- **Amsterdam** - (Ams03)
- **Milan** - (Mil01)
- **Montréal** - (Mon01)

SZRs support 3 node HA in a single data center in that region
{: note}
