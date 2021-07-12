---

copyright:
  years: 2021, 2021
lastupdated: "2021-07-12"

keywords: 

subcollection: Db2oc

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

# Changes to the Lite plan (June/July 2021)

{: #faq_lite_diff}

This is a collection of noteworthy changes to the {{site.data.keyword.Db2_on_Cloud_long}} Lite plan.
{: shortdesc}

## Connectivity

- The hostname is different.
- The port number changes from port 50000 or 50001 to a unique customized port number.
- To encourage data security, less secure connection protocols are disabled. You can only connect to the database using SSL.
  - If you require a non-SSL connection, you may move to the Standard plan and open a support case.

## Credentials

You can obtain credentials in the **Service credentials** tab as soon as you open your service instance. Click **New credential** to get your credentials, hostname, and port number.

Note that you are only allowed to create one service credential per lite instance. Additionally, for security purposes, changes to your password are not displayed in the service credential information.

## VCAP

The VCAP Services JSON file is different. You need to update any applications that consume the VCAP Services JSON file after the migration.

## Console

The console is updated to provide a more refined user experience similar to Standard and Enterprise plans.

## Db2

The Db2 engine is upgraded to v11.5.5, with access to many new features such as external table support and IAM integration.

## Data

To access your data using the updated UI, open your service instance and click the **Go to UI** button to open up the service instance console. From there, you can click on the **data** tab to access your data via the **tables** tab.

On the same page, you can also choose to load data from a file or view other items you've created in the database.

You may choose to access your data through an external program. If you choose to do this you will need:

1. Username and password, obtainable through the **Service credentials** tab when you open up your service instance.

1. Hostname and port, obtainable through the created credentials in the above step, or viewable from the console when you click the **Go to UI** button and navigate to the administrative tab.
1. Certificate, obtainable through the console on the administrative tab by clicking the **Download SSL Certificate** button.
