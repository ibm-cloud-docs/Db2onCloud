---

copyright:
  years: 2014, 2019
lastupdated: "2019-11-18"

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

# Features & specs
{: #fs}

{{site.data.keyword.Db2_on_Cloud_long}} features and specifications are summarized here for your convenience.
{: shortdesc}

| Feature | Supported? | Comments |
|---------|------------|----------|
| Db2 AESE | Y | Db2 v11.1.4.4 |
| Read on Standby | Y | Offsite DR node only |
| Automatic rolling updates | Y | With HA plans |
| Data center location options | Y | [Locations](https://ibm.biz/db2oncloud-locations){:external}. See also: Deployment & scaling durations. |
| BLU in-memory | Y | Default is row, specify `CREATE TABLE..AS COL` for BLU |
| Activity Tracker | [In roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | - |
| Root access provided | N | Use Db2 Hosted if root access is required |
| Copy Database | Y | [Copy Database](/docs/Db2onCloud?topic=Db2onCloud-cp_db) |
| Resource controller support | Y | [Resource controller (RC)](/docs/Db2onCloud?topic=Db2onCloud-rc) |
{: class="simple-tab-table"}
{: caption="Table 1. General" caption-side="top"}
{: #simpletabtable1}
{: tab-title="General"}
{: tab-group="fs"}

| Feature | Supported? | Comments |
|---------|------------|----------|
| Offsite DR | Y | - |
| High availability (2 nodes in 1 zone) | Y | 99.99% uptime SLA |
| Different zones in same data center | [In roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | **Note**: Offsite HADR is available |
| Change Data Capture (CDC) | Y | - |
| Use as HADR from on premises | N | Use CDC. For information, see [How can I migrate or sync data from Db2 to Db2 on Cloud?](https://developer.ibm.com/answers/questions/426111/how-can-i-migrate-from-db2-to-db2-on-cloud/){:external} |
| Autonomous failover - HA | Y | - |
| Autonomous failover - Offsite DR | N | Use button or API |
| IP moves with failover | Y | Local HA only; not offsite HADR |
| RPO: High Availability | 0 s | HA is synchronous |
| RTO: High Availability | Typically 0 - 10 min | With retry code, appears as slowness with Db2 ACR |
| RPO: Offsite node HADR | Typically < 15 s | Offsite DR is asynchronous |
| RTO: Offsite node HADR | < 3 min | Must initiate with console button or API |
{: class="simple-tab-table"}
{: caption="Table 2. High availability & replication" caption-side="top"}
{: #simpletabtable2}
{: tab-title="HA & replication"}
{: tab-group="fs"}

| Feature | Supported? | Comments |
|---------|------------|----------|
| Max RAM and cores | 1 TB RAM, 48 cores | Applies to Precise Performance XL plan |
| Max storage | 11 TB | Applies to Precise Performance XL plan. Disk for both data and logs. |
| Flex: base plan | 4 GB RAM, 1 core, 2 GB disk | - |
| Flex: Max RAM and cores | 128 GB RAM, 32 cores | Need higher specs? Use Precise Performance plan or contact IBM Support. |
| Flex: Max storage | 4 TB | Disk for both data and logs. Need higher specs? Use Precise Performance plan or contact IBM Support. |
{: class="simple-tab-table"}
{: caption="Table 3. System configurations" caption-side="top"}
{: #simpletabtable3}
{: tab-title="System configurations"}
{: tab-group="fs"}

| Feature | Supported? | Comments |
|---------|------------|----------|
| High availability plans | 99.99% | - |
| Single server plans | 99.5% | - |
| Offsite DR node | 99.5% | Must use additional local HA to achieve 99.99% |
| Maintenance policy | Y | [Read details](https://developer.ibm.com/answers/questions/439146/where-can-i-find-detail-about-maintenance-and-noti.html){:external} |
{: class="simple-tab-table"}
{: caption="Table 4. Maintenance policies & SLAs" caption-side="top"}
{: #simpletabtable4}
{: tab-title="Maintenance policies, SLAs"}
{: tab-group="fs"}

| Feature | Supported? | Comments |
|---------|------------|----------|
| HIPAA Ready | Y | All paid plans including Flex. Must request HIPAA mode from IBM Support. |
| HITRUST  | [In roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | Db2 Hosted can be used today for HITRUST |
| International Organization for Standardization (ISO)  | Y | ISO 27001, 27002, 27017, and 27018 |
| Service Organization Controls (SOC) | Y | SOC 2 Type 2 |
| GDPR | Y | - |
| EU Cloud | Y | Use Frankfurt region. Support provided physically in EU. |
| Full list of compliances | Y | [Security compliances](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.security.doc/doc/compliances_summary.html){:external} |
{: class="simple-tab-table"}
{: caption="Table 5. Security compliances" caption-side="top"}
{: #simpletabtable5}
{: tab-title="Security compliances"}
{: tab-group="fs"}

| Feature | Supported? | Comments |
|---------|------------|----------|
| Daily backups | Y | 14 days of daily backups |
| Point-in-time self-serve recovery | Available Nov 15, 2018 | [Point-in-time restore](/docs/Db2onCloud?topic=Db2onCloud-bnr#point-in-time) |
| Backups kept offsite | On request | As of Dec 1, 2018, offsite is default  |
| Keep backup up to 10 yrs | On request | As of Dec 1, 2018. Requires support ticket. |
| Query old data without restore | Y | Must set up [Time Travel Query](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:external} |
{: class="simple-tab-table"}
{: caption="Table 6. Backup & restore" caption-side="top"}
{: #simpletabtable6}
{: tab-title="Backup/restore"}
{: tab-group="fs"}

| Feature | Supported? | Comments |
|---------|------------|----------|
| Single-tenant virtual machine | Y | All paid plans, including Flex, are single-tenant VMs or baremetal. |
| ICIAE | Y | Request from IBM Support. If ICIAE is being requested for an existing service environment, your data must be migrated to your ICIAE environment by IBM Support. |
| VPN | Y | Request from IBM Support |
| On-disk encryption | Y | -  |
| SSL/TLS connections | Y | -  |
| IP whitelisting | Some | Available at Db2 user level. For network level, consider ICIAE or similar.  |
| Key Protect (bring your own key) | Y | [IBM Key Protect](/docs/Db2onCloud?topic=Db2onCloud-key-protect) |
| MIS / Interconnected service | [In roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | - |
| Maximum concurrent connection limit: **Free Lite plan** | Y | Max: 5 connections  |
| Maximum concurrent connection limit: **Paid plans** | N | Unlimited number of connections  |
{: class="simple-tab-table"}
{: caption="Table 7. Networking, security, & VMs" caption-side="top"}
{: #simpletabtable7}
{: tab-title="Networking, security, VMs"}
{: tab-group="fs"}

| Feature | Supported? | Comments |
|---------|------------|----------|
| BYOL discounts | Y | [Announcement](https://ibm.biz/db2oncloud-byol){:external} |
| Available on IBM Cloud | Y | Both subscription and pay-as-you-go |
| Available with software quote order | Y | All plans including Flex. [Parts & details](https://ibm.biz/db2oncloud-parts-public){:external}|
| Available on Hybrid Data Management Platform (HDMP) | Y | Flex plan only. [Details about HDMP](https://www.ibm.com/ca-en/marketplace/hybrid-data-management-platform){:external}|
| Daily billing | Y | Billing for Flex plans is based on peak daily usage. For example, if you scale up from 2 to 8 cores for one hour of a day, you are billed for 8 cores for only that day, and 2 cores for all of the other days of the month. |
| Hourly billing | [In roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | - | 
| Main pricing metric | Monthly | Prices are stated in monthly terms (for example, $189 USD per month). A prorated monthly price is based on the number of days of activated service during the month in which the service was terminated. [Examples](/docs/Db2onCloud?topic=Db2onCloud-plans_pricing#examples) |
{: class="simple-tab-table"}
{: caption="Table 8. Pricing & purchasing" caption-side="top"}
{: #simpletabtable8}
{: tab-title="Pricing & purchasing"}
{: tab-group="fs"}

| Feature | Supported? | Comments |
|---------|------------|----------|
| Dallas | **Deploy**: < 5 minutes. **Scale**: < 45 minutes. | Flex plan only, depending on inventory |
| Other US South | **Deploy**: 1 day. **Scale**: 8 hours. | Some locations shorter than others |
| Frankfurt & London | **Deploy**: < 5 min. **Scale**: 2 hours. | Flex plan only, depending on inventory |
| Other EU | **Deploy**: 3 - 5 days. **Scale**: 1 - 2 days. | Some locations shorter than others |
| Sydney | **Deploy**: < 1 hour. **Scale**: 2 hours. | Flex plan only, depending on inventory |
| Other AP | **Deploy**: 3 - 5 days. **Scale**: 3 - 5 days. | Some locations shorter than others. Lower volumes in AP result in slower infrastructure provisioning times. |
{: class="simple-tab-table"}
{: caption="Table 9. Deployment & scaling durations" caption-side="top"}
{: #simpletabtable9}
{: tab-title="Deployment, scaling durations"}
{: tab-group="fs"}

