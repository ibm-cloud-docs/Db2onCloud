---

copyright:
  years: 2014, 2021
lastupdated: "2022-09-07"

keywords: Lite plan, free plan, faqs

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
{:support: data-reuse='support'}
{:faq: data-hd-content-type='faq'}
{:video: .video}

# FAQs - Lite plan
{: #faq_db2oc_lite}

This is a collection of frequently asked questions (FAQ) about the  {{site.data.keyword.Db2_on_Cloud_long}} Lite plan.
{: shortdesc}

## Will my free plan expire?
{: #fp_faq_expire}
{: faq}
{: support}

You can continue using the free plan for as long as you need. However, you must reactivate the free plan every 45 days. This reactivation process keeps resources available for other users by turning off inactive usage.  

When your plan nears its reactivation date, you will receive a reactivation request at the email address that you provided when creating the instance. Alternatively, you can reactivate in your {{site.data.keyword.Db2_on_Cloud_long_notm}} console.

## Will my data be deleted?
{: #fp_faq_delete}
{: faq}

After you create a Lite instance, you have 45 days before the next reactivation.
* If you do not reactivate, your Lite plan will be disabled, but {{site.data.keyword.cloud_notm}} still has your data. You will then have 60 days to reactivate your account.
* If you don't reactivate within 60 days, your account and data will be deleted.  We will send you multiple emails reminding you to reactivate.


Each time you reactivate, the day counter resets, and you'll have another 45 days before being disabled (and 60 days before deletion).

## How can I download a backup of my data on the Lite plan?
{: #fp_faq_backup}
{: faq}
{: support}

Here are two simple options for backing up Lite plan data:
* Use Db2 tools like the command line tool (`clp`) or IBM Data Studio to do an export. You can then import at another time.
* To quickly make a backup, use the Web console, run a query, then download the results to a CSV file.

## Can I change the email I use for reactivation?
{: #fp_faq_change_email}
{: faq}

Create a new Lite instance with the email you want to use going forward. If needed, first back up your data, delete your current Lite plan instance to create a new one, then load your data. You cannot change the email address associated with an existing Db2 Lite instance if you have only a Lite account with community support. 

## I am having trouble with reactivation. What should I do?
{: #fp_faq_reactivation}
{: faq}
{: support}

If you have trouble with reactivation of a Lite plan instance, you can delete that faulty instance and create a new one. If needed, first back up your data so you can load it to this new instance.  

## I'm getting an error when creating a new instance. What's the problem?
{: #fp_faq_instance}
{: faq}
{: support}

There's a limit of one Lite instance per IAM id. You may see an error 500 message if you try to create a second Lite instance. To create a new Lite plan instance, you must first delete your existing one.

## I'm getting an error when creating a new schema or database. What's the problem?
{: #fp_faq_schema}
{: faq}
{: support}

The free Lite plan does not allow you to create new schemas or databases. There is an existing schema created for you to use. Use that schema.

## Why can’t I open the web console?
{: #fp_faq_console}
{: faq}
{: support}

If the Db2 web console does not load or returns an error message, try the following steps:
* Go to the service page to check whether your Lite instance has expired. The **Open Console** button no longer appears for expired instances. Delete the expired instance and create a new one.
* Try using the direct URL to open the console to check for errors. Select the **Service credentials** tab from your service page and expand the credentials that you want to view. If there are no existing credentials, click **New credential**. Use the values in the `https_url`, `username`, and `password` to open the web console.
*  To reset the password, select the **Service credentials** tab from your service page and then delete the existing service lite-tier service credential.  Then click **New credential** to generate a new password for the existing username. 
* When you create a Lite instance, be sure to provide an email address so you receive reactivation notices and password reset notices. 
* If your use of {{site.data.keyword.Db2_on_Cloud_long_notm}} exceeds the purpose provided by a Lite account with free support, upgrade to a paid account with [basic, advanced, or premium support](/docs/get-support?topic=get-support-support-plans){: external} to open cases for technical issues. 

## What options do I have for support?
{: #fp_faq_support}
{: faq}
{: support}

The free Lite plan for {{site.data.keyword.Db2_on_Cloud_long_notm}}, intended for prototyping and demoing applications, has only community support available to help you. You cannot get assistance with your free Lite plan by opening a support ticket. For example, if you need help with a Db2 usage question, query optimization, or a syntax error, review the available [Communities](/docs/Db2onCloud?topic=Db2onCloud-communities){: external} and the list of [{{site.data.keyword.Db2_on_Cloud_short}} Resources](https://www.ibm.com/cloud/db2-on-cloud/resources){: external}. 