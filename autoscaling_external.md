# Auto-scaling

Autoscaling is designed to respond to the short-to-medium term trends in storage usage on your db2oc deployment. When enabled, your deployment is checked at an interval you specify. If the storage is below the threshold value then the storage is automatically scaled up. To keep an eye on your resources, use the MonitoringIBM Cloud® Monitoring integration, which provides metrics for disk space.

You can set your db2oc deployment to autoscale **disk**.


## General Autoscaling Parameters

- When to scale, based on usage over time.
- A hard limit on scaling, your deployment stops autoscaling at the limit.

![paras.png](images/autoscaling_UI.png)

<Figure 1. Example Autoscaling panel>


## ****Autoscaling Considerations****

- **Storage cannot be scaled down.**
- Each increment is 10% of your storage size. The minimum increase is 20GB.
- Limits:
    - We support autoscaling up to 4 TB.
- If you occasionally or rarely increase storage on your deployment, then you can manually scale your deployment.
- A few scaling operations can be more long running than others. Drastically increasing Disk can take longer than smaller increases to account for provisioning more underlying hardware resources.


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
- `limit_mb_per_member` has to be a multiple of 20Gi, eg. 4096000 MB = 4000Gi. And it’s smaller or equal to 4096000 MB.

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
