# Loading data from IBM Cloud Object Storage


## Using Console

You can load data from IBM Cloud Object Storage (COS) into IBM® Db2® on Cloud by using the Console.

### Create the necessary credentials on the COS bucket to allow Console to access the data

1. Access the COS Bucket on the IBMCloud Dashboard by clicking on the name

    ![Access COS Bucket](./COS_Bucket.png "Select COS Bucket")

2. Create Credentials on the COS bucket so Db2 Console can access the data.

    1. Select `Service Credentials`
    2. Click on `New Credentials`
    3. Enter `Name` for the Service Credential
    4. Select the appropriate role
    5. Ensure `Include HMAC Credential` is enabled

    ![Create Service Credentials](./Service_Cred_Create.png "Create Service Credentials")

3. Get the `Access key` and `Secret access key` from the Credentials 

    1. Expand the Credential
    2. Note down the `access_key_id` and `secret_access_key`

    ![Get Keys](./get_keys.png "Get Access Keys")

4. Open the Db2 Console to the load data page

    1. Click on `Data` on the left menu
    2. Click on `Load Data` on the top tab
    3. Click on `Cloud Object Storage`
    4. Pick the `COS Authentication Endpoint` that matches your bucket
    5. Enter the `access_key_id` from above for `Access key`
    6. Enter the `secret_access_key` from above for `Secret access key`
    7. Click on `Browse Files` to select the file you want to load from

    ![Load Data page](./Load_Data.png "Load Cos Data")

## External Tables

You can load data from IBM Cloud Object Storage (COS) into IBM® Db2® on Cloud by using the built-in External Tables functionality.


Here's an example SQL statement that inserts COS data into a {{site.data.keyword.dashdbshort_notm}} table by using External Tables:

```
INSERT INTO <table-name> SELECT * FROM EXTERNAL '<mys3file.txt>' USING
  (CCSID 1208 s3('s3-api.us-geo.objectstorage.softlayer.net',
  '<S3-access-key-ID>',
  '<S3-secret-access-key>',
  '<my_bucket>'
     )
  )
```
