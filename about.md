---

copyright:
  years: 2014, 2023
lastupdated: "2024-12-20"

keywords: 

subcollection: Db2onCloud

---

 
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:warning .warning}

# About
{: #about}

## Plans and configurations
{: #ab_plans_cfgs}

For information about the plans and configurations supported on IBM Cloud, see [here](https://cloud.ibm.com/docs/Db2onCloud?topic=Db2onCloud-about). 


This set of documentation covers the detailed commands and reference topics for the Db2 engine that powers Db2 on Cloud. To find the IBM Cloud documentation for the offering, see [here](https://cloud.ibm.com/docs/Db2onCloud?topic=Db2onCloud-about). The IBM Cloud documentation covers the high-level functionality for the cloud offering, and refers back to this set of documentation where appropriate.{: warning}
=======

### Standard Plan

- Base instances start at 8 GB RAM x 20 GB storage on shared compute slices
- 100 GB of free backup storage for up to 14 days of backups

### Enterprise Plan

- Base instances start at 4 vCPU x 16 GB RAM x 20 GB storage on dedicated compute slices
- 1 TB of free backup storage for up to 14 days of backups

### Performance Plan

- Base configuration start at 4vCPU x 16GB RAM x 50GB Storage on dedicated compute slices
- 2-node High Availability
- Customizable IOPS Scaling

## Supported data centers (Performance)

The Performance plan is supported in the following data center geographies:

- **Dallas** - (us-south-1, us-south-2, us-south-3)
- **Washington** - (us-east-1, us-east-2, us-east-3)


## Supported data centers (Standard and Enterprise)
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

MZRs support 3 node HA in 3 different data centers in that region.
{: note}

### Single-zone region (SZR)
- **Amsterdam** - (Ams03)
- **Milan** - (Mil01)
- **Montréal** - (Mon01)

SZRs support 3 node HA in a single data center in that region.
{: note}

### EU-Supported (MZR)
- **Frankfurt 02** - (Fra02, Fra04, Fra05)

EU-Supported MZR supports 3 node HA in 3 different data centers in that region.
{: note}

