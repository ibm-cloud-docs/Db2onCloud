---

copyright:
  years: 2021, 2021
lastupdated: "2021-09-29"

keywords: 

subcollection: Db2whc

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

# FAQ - Lite plan migration

{: #faq_lite}

This is a collection of frequently asked questions (FAQs) about migrating the {{site.data.keyword.Db2_on_Cloud_long}} on Cloud Lite plan.
{: shortdesc}

## What do I have to do during the migration?
{: #q_migrate}

The migration will be done for you. The process requires a 24-hour outage window, during which your instance will be unavailable. Once the migration completes, you will be notified that your instance is ready for use again.

## What's changing with this migration?
{: #q_changes}

### Connectivity

- The hostname is different.
- The port number changes from port 50001 to a unique customized port number.
- To encourage data security, less secure connection protcols are disabled. You can only connect to the database using SSL.
- If you require a non-SSL connection, you may move to the Standard plan and open a support case.

### Console

The console is revamped to provide a more refined user experience similar to Standard and Enterprise plans.

### VCAP

The VCAP Services JSON file will be different. You will need to update any applications that consume the VCAP Services JSON file after the migration. For more information about the Standard and Enterprise VCAP Services JSON file, see Connectivity options.

## What will I need to do after the upgrade to a new plan?

You need to retrieve the host name and port number, which will have changed after the upgrade. Once the migration completes you will need to log in to your instance still with the same username and password to retrieve the new hostname and port number in the VCAP.

## Will there be a change in cost after the migration?

No. The Lite plan will still be free after the migration procedure.

## Can I continue using non-SSL connections after the migration?

No. To protect the security of all users' data, the non-SSL port is blocked on the new {{site.data.keyword.Db2_on_Cloud_short}} Lite Tier systems. Due to the multi-tenant nature of the plan, we are unable to open the non-SSL port. If you require non-SSL connections, please upgrade to the Standard plan and open a [support case](https://cloud.ibm.com/unifiedsupport/supportcenter).

## Migration Schedule for {{site.data.keyword.Db2_on_Cloud_long}} Lite plan

| Hostname | New Connection String | Migration Date |
|--------------|-------|-------------|
| dashdb-txn-sbox-yp-lon02-15 | jdbc:db2://21fecfd8-47b7-4937-840d-d791d0218660.bs2io90l08kqb1od8lcg.databases.appdomain.cloud:31864 | 05/10/2021 |
| dashdb-txn-sbox-yp-lon02-06 | jdbc:db2://2d46b6b4-cbf6-40eb-bbce-6251e6ba0300.bs2io90l08kqb1od8lcg.databases.appdomain.cloud:32328 | 05/10/2021 |
| dashdb-txn-sbox-yp-lon02-13 | jdbc:db2://3883e7e4-18f5-4afe-be8c-fa31c41761d2.bs2io90l08kqb1od8lcg.databases.appdomain.cloud:31498 | 05/10/2021 |
| dashdb-txn-sbox-yp-lon02-07 | jdbc:db2://815fa4db-dc03-4c70-869a-a9cc13f33084.bs2io90l08kqb1od8lcg.databases.appdomain.cloud:30367 | 05/10/2021 |
| dashdb-txn-sbox-yp-lon02-02 | jdbc:db2://824dfd4d-99de-440d-9991-629c01b3832d.bs2io90l08kqb1od8lcg.databases.appdomain.cloud:30119 | 06/10/2021 |
| dashdb-txn-sbox-yp-lon02-04 | jdbc:db2://8e359033-a1c9-4643-82ef-8ac06f5107eb.bs2io90l08kqb1od8lcg.databases.appdomain.cloud:30120 | 06/10/2021 |
| dashdb-txn-sbox-yp-lon02-01 | jdbc:db2://ea286ace-86c7-4d5b-8580-3fbfa46b1c66.bs2io90l08kqb1od8lcg.databases.appdomain.cloud:31505 | 06/10/2021 |
| dashdb-txn-sbox-yp-dal09-08 | jdbc:db2://125f9f61-9715-46f9-9399-c8177b21803b.c1ogj3sd0tgtu0lqde00.databases.appdomain.cloud:30426 | 06/10/2021 |
| dashdb-txn-sbox-yp-dal09-12 | jdbc:db2://19af6446-6171-4641-8aba-9dcff8e1b6ff.c1ogj3sd0tgtu0lqde00.databases.appdomain.cloud:30699 | 07/10/2021 |
| dashdb-txn-sbox-yp-dal09-14 | jdbc:db2://6667d8e9-9d4d-4ccb-ba32-21da3bb5aafc.c1ogj3sd0tgtu0lqde00.databases.appdomain.cloud:30376 | 07/10/2021 |
| dashdb-txn-sbox-yp-dal09-11 | jdbc:db2://9938aec0-8105-433e-8bf9-0fbb7e483086.c1ogj3sd0tgtu0lqde00.databases.appdomain.cloud:32459 | 07/10/2021 |
| dashdb-txn-sbox-yp-dal09-04 | jdbc:db2://b1bc1829-6f45-4cd4-bef4-10cf081900bf.c1ogj3sd0tgtu0lqde00.databases.appdomain.cloud:32304 | 07/10/2021 |
| dashdb-txn-sbox-yp-dal09-10 | jdbc:db2://b70af05b-76e4-4bca-a1f5-23dbb4c6a74e.c1ogj3sd0tgtu0lqde00.databases.appdomain.cloud:32716 | 08/10/2021 |
| dashdb-txn-sbox-yp-dal09-03 | jdbc:db2://fbd88901-ebdb-4a4f-a32e-9822b9fb237b.c1ogj3sd0tgtu0lqde00.databases.appdomain.cloud:32731 | 08/10/2021 |
{: caption="Table 1. Migration Schedule" caption-side="top"}