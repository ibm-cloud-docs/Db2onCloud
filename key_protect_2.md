---

copyright:
  years: 2014, 2020
lastupdated: "2020-05-05"

keywords: db2, Db2 on Cloud, bring your own key, byok, crypto-shredding

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

# Key Protect integration
{: #key-protect-v2}

The data that you store in Db2 when using the Enterprise plan is encrypted by default by using randomly generated keys. If you need to control the encryption keys, you can use [{{site.data.keyword.keymanagementservicelong_notm}}](/docs/key-protect?topic=key-protect-integrate-services) to create, add, and manage encryption keys. Then, you can associate those keys with your {{site.data.keyword.databases-for}} deployment to encrypt your Db2 databases.

To get started, you need [{{site.data.keyword.keymanagementserviceshort}}](https://cloud.ibm.com/catalog/services/key-protect){: external} provisioned on your {{site.data.keyword.cloud_notm}} account.

## Creating or adding a key in {{site.data.keyword.keymanagementserviceshort}}
{: #kp-create-add}

Navigate to your instance of {{site.data.keyword.keymanagementserviceshort}} and [generate or enter a key](/docs/key-protect?topic=key-protect-getting-started-tutorial).

## Granting service authorization
{: #kp-grant}

Authorize {{site.data.keyword.keymanagementserviceshort}} for use with {{site.data.keyword.databases-for}} deployments:

1. Open your {{site.data.keyword.cloud_notm}} dashboard.
1. From the menu bar, select **Manage > Access (IAM)**.
1. In the side navigation, select **Authorizations**. Click **Create**.
1. In the _Source service_ menu, select the service of the deployment. For example, **Db2**.
1. In the _Source service instance_ menu, select **All service instances**.
1. In the _Target service_ menu, select **Key Protect**.
1. In the _Target service instance_ menu, select the service instance to authorize.
1. Enable the `Reader` role. Click **Authorize**.

## Using the Key Protect key
{: #kp-use}

After you grant your {{site.data.keyword.databases-for}} deployments permission to use your keys, you supply the [key name or CRN](/docs/key-protect?topic=key-protect-view-keys) when you provision a deployment. The deployment uses your encryption key to encrypt your data.

If you provision a deployment through the CLI or API, the key protect key needs to be identified by its full CRN, not just its ID. A key protect CRN is in the format `crn:v1:<...>:key:<id>`.
{: tip}

## Deleting the deployment
{: #kp-delete}

If you delete a deployment that is protected with a Key Protect key, the deployment remains registered against the key for the duration of the soft-deletion period (up to 9 days). If you need to delete the key in the soft-deletion period, you have to [force delete](/docs/key-protect?topic=key-protect-delete-keys) the key. After the soft-deletion period the key can be deleted without the force. You can check the [association between the key and your deployment](/docs/key-protect?topic=key-protect-view-protected-resources) to determine when you can delete the key.

## Cryptoshredding
{: #kp-cryptoshred}

Cryptoshredding is a destructive action. Once the key is deleted your data is unrecoverable.
{: important}

{{site.data.keyword.keymanagementserviceshort}} allows you to [initiate a force delete](/docs/key-protect?topic=key-protect-delete-keys) of a key that is in use by {{site.data.keyword.cloud}} services, including your {{site.data.keyword.databases-for}} deployments. This action is called cryptoshredding. Deleting a key that is in use on your deployment locks the disks containing your data and disables your deployment. You are still able to access the UI and some metadata such as security settings in the UI, CLI, and API but you are not able to access any of the databases or data contained within them. Key deletion is [sent to the Log Analysis Activity Tracker](/docs/key-protect?topic=key-protect-at-events) as `kms.secrets.delete`.