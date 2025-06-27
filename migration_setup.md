---
copyright:
  years: 2025
lastupdated: "2025-06-26"

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

# Migration Initialization
{: #migration_initialization}

To begin migrating your Db2 on Cloud deployment to a newer system version, follow these steps:

1. Provision your Db2 on Cloud resource from the IBM Cloud catalog if you haven't already.
2. In the **IBM Cloud console**, navigate to your list of resources and click the instance you want to upgrade.
3. At the top of the instance page, look for the notification banner that says **System upgrade available**, onn the right-hand side of the banner, click **Learn More**.
![System upgrade notification banner example](images/migration_learn_more.png)
{: caption="Example of the upgrade notification banner in the console." caption-side="bottom"}
4. You will be redirected to the **Upgrade Db2 Systems** page, in the upgrade interface, click **Create Instance**. A popup will show showing the parent formation and the new formation's name, select the location youd like your instance to be provisioned in. Click **Create** to start provisioning your new upgraded environment.
![Upgrade Db2 Systems page example](images/migration_create_new_instance.png)
{: caption="Example of the Upgrade Db2 Systems page where you create the new instance." caption-side="bottom"}
![Create Instance Confirm](images/migration_create_confirm.png)
{: caption="Confirm location and create new instance." caption-side="bottom"}

{:note}
Any autoscale settings in **Classic** will need to be recreated in the **Performance** plan after the migration is complete.

5. When the new formation is created, the migration process begins automatically. To track the migration progress:
   - Click the new formation you created.
   - Click the **View Details** button to see the current status and progress of the migration.

![Migration view details button](images/migration_view_details.png)
{: caption="Click View Details button." caption-side="bottom"}
![Migration track migration process](images/migration_complete_restore.png)
{: caption="Track migration process." caption-side="bottom"}
