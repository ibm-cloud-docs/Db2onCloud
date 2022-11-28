---

copyright:
  years: 2014, 2022
lastupdated: "2022-11-22"

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



# Auto-scaling


When you enable autoscaling, the storage on your Db2 on Cloud instance will automatically be scaled up if your storage use exceeds the threshold you specify. For example, you can choose to scale up your storage by 20GB if more than 90% of your storage is in use for a period of 15 minutes.

To monitor your storage usage, use the IBM Cloud® Monitoring integration, which provides metrics for disk space.



## General Autoscaling Parameters

- When to scale, based on usage over time.
- A hard limit on scaling, your deployment stops autoscaling at the limit.

![paras.png](images/autoscaling_UI.png)

<Figure 1. Example Autoscaling panel>


## ****Autoscaling Considerations****

- **Storage cannot be scaled down.**
- Each increment is 10% of your storage size. The minimum increase is 20GB.
- Storage can be auto-scaled up to a limit of 4 TB.
- You must have the IAM Operator, Editor or Administrator authority in order to use this feature.
- If you rarely increase storage on your deployment, you might want to manually scale your deployment rather than enabling the auto-scaling feature.
- Scaling is an online operation.
- Some scaling operations can be more long running than others. Significantly increasing the storage size can take longer than increasing it by a small amount because additional underlying hardware resources must be provisioned.



## ****Configuring Autoscaling in the UI****

The Autoscaling panel is on the Administration tab of your deployment's console page.

### To enable autoscaling
1. Click **Edit**  
2. Check **Enable storage autoscaling**
3. Enter your desired parameter values.
4. Be sure to click **Save** for your configuration to be saved and your changes to take effect.

![autoscaling_step1.png](images/autoscaling_step1.png)
<br>
![autoscaling_step2.png](images/autoscaling_step2.png)


### To disable autoscaling
1. Click **Edit**  
2. Uncheck **Enable storage autoscaling**.
3. Click **Save Changes** to save the configuration.


## ****Configuring Autoscaling in the API****

You can get the autoscaling parameters for your deployment through the API by sending a `GET` request to the [/deployments/{id}/groups/{group_id}/autoscaling](https://cloud.ibm.com/apidocs/cloud-databases-api/cloud-databases-api-v5#getautoscalingconditions) endpoint.

```bash
curl -X GET https://api.{region}.databases.cloud.ibm.com/v5/ibm/deployments/{id}/groups/{group_id}/autoscaling \
-H 'Authorization: Bearer <>'
```

To enable and set the autoscaling parameters for your deployment through the API, send a `PATCH` request to the endpoint.

- Enabling autoscaling works by setting the `scalers` (`capacity`) to `true`.
- `limit_mb_per_member` value has to be a multiple of 20Gi, eg. 4096000 MB = 4000Gi. The value must also be less than or equal to 4096000 MB.

```bash
curl -X PATCH https://api.{region}.databases.cloud.ibm.com/v5/ibm/deployments/{id}/groups/{group_id}/autoscaling
-H 'Authorization: Bearer <>' \
-H 'Content-Type: application/json' \
-d '{
    "autoscaling": {
        "disk": {
            "scalers": {
                "capacity": {
                    "enabled": true,
                    "free_space_less_than_percent": 20,
		    "above_percent": 90
                }
            },
            "rate": {
		"increase_percent": 10.0,
		"period_seconds": 300,
                "limit_mb_per_member": 4096000,
		"units": "mb"
        }
        }
    }
}'
```
