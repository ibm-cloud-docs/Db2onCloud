# Recovery steps after auto-upgrade

Customers on legacy plans who have not started the upgrad process will be automatically upgraded in a rolling fashion starting Nov 11th, 2020.

The following document describes the flow to recover the upgraded system once auto-upgrade has been initiated.


## Recovery
1. Login to the IBM Cloud account where the Legacy Db2 on Cloud system was provisioned.  [http://cloud.ibm.com]

![list of instances](images/recovery_instance_list_blur.png "List of instances"){: caption="Figure 1. Highlight your service instance" caption-side="bottom"}

2. If your legacy instance is listed under `Cloud Foundry services`, it will first need to be migrated to a resource group. 

![Cloud Foundry Instance](images/recovery_cf_blur.png "Cloud Foundry Instance"){: caption="Figure 2. Cloud Foundry Instance" caption-side="bottom"}

 - To migrate, click on the instance and then click on `Migrate`.  Once migrated the Db2 instance will now be listed under `Services`
        ![Cloud Foundry Migration](images/recovery_cf_migration_blur.png "Cloud Foundry Migration"){: caption="Figure 3. Migrating Cloud Foundry Instance" caption-side="bottom"}


3. Copy the CRN of your legacy instance under `Services`
   
![Copy the CRN](images/recovery_CRN_blur.png "Copy the CRN"){: caption="Figure 4. Copy the CRN" caption-side="bottom"}


4. Order a new Standard or Enterprise instance, specifing the above CRN in the recovery field to start 
   the recovery process.

![Intiate the Recovery](images/recovery_v2.png "Initiate the recovery"){: caption="Figure 5. Initiate the recovery" caption-side="bottom"}

5. The new Db2 service instance will be visible under `Services`, however it will not be ready for use until the owner of the account is notified via email that it is available for use

6. The time to recovery depends on the size of the database but in most cases will be completed well under 24 hours.










