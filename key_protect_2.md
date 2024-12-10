---

copyright:
  years: 2014, 2021
lastupdated: "2023-06-20"

keywords: db2, Db2 on Cloud, bring your own key, byok, crypto-shredding, kyok, keep your own key

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

# Integrating your data and keys 
{: #key-management-services}

The data that you store in Db2 when using the Standard or Enterprise plan is encrypted by default by using randomly generated keys. If you need to control the encryption keys, you can use [{{site.data.keyword.keymanagementservicelong_notm}}](/docs/key-protect?topic=key-protect-integrate-services) or [{{site.data.keyword.hscrypto}}](/docs/hs-crypto?topic=hs-crypto-get-started)to create, add, and manage encryption keys. Then, you can associate those keys with your Db2 on Cloud deployment to encrypt your Db2 databases.

{{site.data.keyword.keymanagementservicelong_notm}} helps you provision encrypted keys for apps across {{site.data.keyword.cloud_notm}} services. As you manage the lifecycle of your keys, you can benefit from knowing that your keys are secured by FIPS 140-2 Level 3 certified cloud-based hardware security modules (HSMs) that protect against the theft of information.

{{site.data.keyword.hscrypto}} is a single-tenant, dedicated HSM that is controlled by you. The service is built on FIPS 140-2 Level 4-certified hardware, the highest offered by any cloud provider in the industry.

To get started, you need to provision a [{{site.data.keyword.keymanagementserviceshort}}](https://cloud.ibm.com/catalog/services/key-protect){: external} instance or a [{{site.data.keyword.hscrypto}}](https://cloud.ibm.com/catalog/services/hs-crypto){: external} instance on your {{site.data.keyword.cloud_notm}} account.

## Creating or adding a key in the key management service
{: #kp-create-add}

To add a key in {{site.data.keyword.keymanagementserviceshort}}, navigate to your instance of {{site.data.keyword.keymanagementserviceshort}} and [generate or enter a key](/docs/key-protect?topic=key-protect-getting-started-tutorial).

To add a key in {{site.data.keyword.hscrypto}}, navigate to your instance of {{site.data.keyword.hscrypto}} and [generate a key](/docs/hs-crypto?topic=hs-crypto-get-started).

## Granting service authorization
{: #kp-grant}

Authorize {{site.data.keyword.keymanagementserviceshort}} for use with Db2 as a Service deployments:

1. Open your {{site.data.keyword.cloud_notm}} dashboard.
1. From the menu bar, select **Manage > Access (IAM)**.
1. In the side navigation, select **Authorizations**. Click **Create**.
1. In the _Source service_ menu, select the service of the deployment. For example, **Db2**.
1. In the _Source service instance_ menu, select **All service instances**.
1. In the _Target service_ menu, select **Key Protect** or **Hyper Protect Crypto Services**.
1. In the _Target service instance_ menu, select the service instance to authorize.
1. Enable the `Reader` role. Click **Authorize**.

## Using the key encryption key
{: #kp-use}

After you grant your Db2 on Cloud deployments permission to use your keys, you supply the key name or CRN in  [{{site.data.keyword.keymanagementserviceshort}}](/docs/key-protect?topic=key-protect-view-keys) or [{{site.data.keyword.hscrypto}}](/docs/hs-crypto?topic=hs-crypto-view-keys) when you provision a deployment. The deployment uses your encryption key to encrypt your data.

If you provision a deployment through the CLI or API, the key needs to be identified by its full CRN, not just its ID. A CRN is in the format `crn:v1:<...>:key:<id>`.
{: tip}

## Deleting the deployment
{: #kp-delete}

If you delete a deployment that is protected with a key, the deployment remains registered against the key for the duration of the soft-deletion period (up to 9 days). If you need to delete the key in the soft-deletion period, you have to force delete the key using  [{{site.data.keyword.keymanagementserviceshort}}](/docs/key-protect?topic=key-protect-delete-keys) or  [{{site.data.keyword.hscrypto}}](/docs/hs-crypto?topic=hs-crypto-delete-keys). After the soft-deletion period the key can be deleted without the force. You can check the [association between the key and your deployment](/docs/key-protect?topic=key-protect-view-protected-resources) to determine when you can delete the key.

## Cryptoshredding
{: #kp-cryptoshred}

Cryptoshredding is a destructive action. Once the key is deleted your data is unrecoverable.
{: important}

{{site.data.keyword.keymanagementserviceshort}} or {{site.data.keyword.hscrypto}} allows you to initiate a force delete of a key that is in use by {{site.data.keyword.cloud}} services using [{{site.data.keyword.keymanagementserviceshort}}](/docs/key-protect?topic=key-protect-delete-keys) or [{{site.data.keyword.hscrypto}}](/docs/hs-crypto?topic=hs-crypto-delete-keys), including your Db2 on Cloud deployments. This action is called cryptoshredding. Deleting a key that is in use on your deployment locks the disks containing your data and disables your deployment. You are still able to access the UI and some metadata such as security settings in the UI, CLI, and API but you are not able to access any of the databases or data contained within them. Key deletion is sent to the Log Analysis Activity Tracker as `kms.secrets.delete` using [{{site.data.keyword.keymanagementserviceshort}}](/docs/key-protect?topic=key-protect-at-events) and as `hs-crypto.secrets.delete` using [{{site.data.keyword.hscrypto}}](/docs/hs-crypto?topic=hs-crypto-at-events).
