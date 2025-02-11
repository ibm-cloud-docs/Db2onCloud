---

copyright:
  years: 2014, 2020, 2021, 2022
lastupdated: "2025-02-05"

keywords: provision cloud database, database with terraform, provisioning parameters, db2 on cloud, db2

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
{:video: .video}

# Provision a service instance
{: #provisioning}

To deploy an {{site.data.keyword.Db2_on_Cloud_long}} service, you need to create a {{site.data.keyword.Db2_on_Cloud_short}} service instance. 
{: shortdesc}

You can provision a deployment by visiting the service's catalog page or by specifying the service ID to the command line, or to the API. The deployment type is determined by the service ID, which you must specify when you create a {{site.data.keyword.Db2_on_Cloud_short}} deployment by using the command line or API. 

| Deployment Type | Catalog Page | Service ID | Plan IDs |
|-----------------|--------------|------------|----------|
| {{site.data.keyword.Db2_on_Cloud_short}} |[Link](https://cloud.ibm.com/catalog/services/db2){: external} | dashdb-for-transactions | dashDBNebula, dashDBStandard |

## Using the catalog
{: #prov_catalog}

When you create the deployment from the catalog, you need to specify the following parameters.

1. **Service name** - The name can be any string and is the name that is used on the web and in the command line to identify the new deployment.

1. **Region** - The region in which the deployment resides.

1. **Backup Location** - The location of the deployment's backups. Users can choose **Cross Regional** or **Regional** backups. Cross Regional backups can be stored across multiple regions in one zone. Whereas, Regional backups can be stored in one region only.

1. **Resource group** - If you are organizing your services into resource groups, you can specify the resource group in this field. Otherwise, you can leave it at default.

1. **KMS instance** and **disk encryption key** - If you use Key Protect or Hyper Protect Crypto Services, an instance and key can be selected to encrypt the deployment's disk. If you do not use your own key, the deployment automatically creates and manages its own disk encryption key using the Key Protect service. If you would like to use HPCS for encryption, you must [provision an HPCS instance](docs/hs-crypto?topic=hs-crypto-provision&interface=ui) and generate or import a key. Currently, HPCS is not EU-Cloud enabled. 

1. **Backup Encryption Key** - If you use Backup Encyrption Key, you can provide your own KMS instance and key in order to encrypt your backups. This is an optional parameter, and if not provided the default KMS instance and key will be used.

1. **CPU allocation** - Choose dedicated compute resources for your deployment. With dedicated cores, your resource group is given a single-tenant host with a guaranteed minimum reserve of cpu shares. Your deployments are then allocated the number of CPUs you specify. This defaults to the `standard plan` if not specified in the provisioning request by using the API or CLI.

1. **Endpoints** - You can configure the types Service Endpoints on your deployment. The default is that connections to your deployment can be made from the public network.

1. **High Availability** - whether the services should be Highly Available

1. **Oracle compatibility** - whether the service instance should have Oracle compatibility enabled

After selecting the appropriate settings, click **Create** to start the provisioning process.

## Using the command line
{: #prov_cl}

The {{site.data.keyword.cloud_notm}} CLI tool is what you use to communicate with {{site.data.keyword.cloud_notm}} from your terminal or command line. For more information, see [Download and install {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started).

To create a {{site.data.keyword.databases-for}} deployment, you use the CLI to request a service instance with the service ID of the database (or messaging queue) that you want to provision.

Run the following command template:

```
ibmcloud resource service-instance-create <service-name> <service-id> <service-plan-id> <region> --service-endpoints <SERVICE_ENDPOINTS_TYPE>
```
{: codeblock}

More general information about this command is available in the [CLI reference for resource groups]().

When the command is run, the database deployment begins. The database takes some time to deploy. You can check on its progress on your {{site.data.keyword.cloud_notm}} dashboard or you can run the following command:

```
ibmcloud resource service-instance-create <service-name>
```
{: codeblock}

This command reports the current state of the service instance.

## Additional flags and parameters
{: #prov_flags_parms}

The `--service-endpoints` flag allows you to specify which types of [service endpoints]() to include in your deployment. Its default is that connections to your deployment can be made from the public network. Possible values are `public`, `private`, `public-and-private`. If the flag is omitted, the default is a `public` endpoint.

The following example command specifies a service endpoint:
```
ibmcloud resource service-instance-create <service-name> --service-endpoints <endpoint-type>
```
{: codeblock}

The `service-instance-create` command supports a `-p` flag, which allows [additional parameters](#prov_add_parms) to be passed to the provisioning process. The parameters are in JSON format. One such parameter value is the Cloud Resource Name (CRN), which uniquely identifies a resource in the cloud. All parameter names and values are passed as strings.

## Provisioning through the Resource Controller API
{: #prov_rc_api}

You can provision new deployments by using the Resource Controller API. However, in order to use the Resource Controller API, you need some additional preparation.

1. [Obtain an IAM token from your API token]().
    
1. You must know the ID of the resource group to which you would like to deploy. This information is available through the [{{site.data.keyword.cloud_notm}} CLI](). You can find a list of resource groups with `ibmcloud resource groups` and the ID of a resource group with `ibmcloud resource group`.
1. You must know the region to which you would like to deploy.

After you have all of the information, the following create request is a `POST` to the `https://resource-controller.cloud.ibm.com/v2/resource_instances` endpoint:

```
curl -X POST \
  https://resource-controller.cloud.ibm.com/v2/resource_instances \
  -H 'Authorization: Bearer <>' \
  -H 'Content-Type: application/json' \
    -d '{
    "name": "my-instance",
    "target": "bluemix-us-south",
    "resource_group": "5g9f447903254bb58972a2f3f5a4c711",
    "resource_plan_id": "dash
  }'
```
{: codeblock}

The parameters `name`, `target`, `resource_group`, and `resource_plan_id` are all required. If needed, you can send [additional parameters](#prov_add_parms) in the request body.

More information on the Resource Controller API is found in its [API Reference]().



## List of additional parameters
{: #prov_add_parms}

- `backup_id` - A CRN of a backup resource to restore from. The backup must have been created by a database deployment with the same service ID. The backup is loaded after provisioning and the new deployment starts up that uses that data. A backup CRN is in the format `crn:v1:<...>:backup:<uuid>`. If omitted, the database is provisioned empty.
- `backup_location` - The location of the deployment's backups.
- `disk_encryption_key_crn` - The CRN of a [KMS key](), which is then used for disk encryption. A KMS CRN is in the format `crn:v1:<...>:key:<id>`.
- `backup_encryption_key_crn` - The CRN of a [KMS key](), which is then used for backup encryption. A KMS CRN is in the format `crn:v1:<...>:key:<id>`. 
   To use a key for your backups, you must first enable the [service-to-service delegation]()
- `members_cpu_allocation_count` - Enables and allocates the number of specified dedicated cores to your deployment. For example, to use two dedicated cores per member, use `"members_cpu_allocation_count":"2"`. If omitted, the default value "Shared CPU" uses compute resources on shared hosts.  

- `service-endpoints` - Selects the types [Service Endpoints]() supported on your deployment. Options are `public`, `private`, or `public-and-private`. If omitted, the default is `public`. Note that in the CLI, `service-endpoints` is a flag, and not a parameter.

`backup_encryption_key_crn` is NOT applicable to performance plans.  For performance plans, backup will be encrypted with the same key as disk_encryption_key_crn.  If disk_encryption_key_crn is not specified, it'll use the default provider managed key. {: note}

## List of additional parameters (for performance plans only)

- `timezone` - the timezone that your database and the underlying operating system should use. Any timezone identifier accepted by Linux (e.g. `America/Toronto`) will be accepted here. If omitted, the default is UTC.

<!--
- `version` - The version of the database to be provisioned. If omitted, the database is created with the most recent major and minor version.
-->


<!--
- `members_memory_allocation_mb` - Total amount of memory to be allocated to the instance. For example, if the value is "6144", and there are three database members, then the deployment gets 6 GB of RAM total, giving 2 GB of RAM per member. If omitted, the default value for the database type is used.
- `members_disk_allocation_mb` - Total amount of disk to be shared between the database members within the database. For example, if the value is "30720", and there are three members, then the deployment gets 30 GB of disk total, giving 10 GB of disk per member. If omitted, the default value for the database type is used.
-->


<!-- - `{"remote_leader_id": "crn:v1:..."}` - parameter only for {{site.data.keyword.Db2_on_Cloud_long}}.-->
