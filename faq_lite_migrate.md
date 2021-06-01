---

copyright:
  years: 2021, 2021
lastupdated: "2021-06-01"

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
