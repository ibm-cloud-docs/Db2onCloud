# Changes after the upgrade to Standard/Enterprise Plans



## Changes from the Legacy plan to Standard or Enterprise Plans

 Customers should be aware of the following changes:
### Connectivity Changes:

   1. The hostname of the Standard or Enterprise Plan will be different

   2. The port number will change from port 50000 to a unique port number

   3. Connections to the database will default to SSL
   
   4. Console/REST API hostname is different from JDBC URL 

For more information see [Connectivity options](https://cloud.ibm.com/docs/Db2onCloud?topic=Db2onCloud-connect_options)

### Credential Changes
   
   1. New credentials will need to created in IBMCloud to access the database instance. 

   2. Credentials on IBM Cloud will not include bluadmin but the user still exists to connect to the database

For more information on creating credentials see [Connectivity options](https://cloud.ibm.com/docs/Db2onCloud?topic=Db2onCloud-connect_options)

### VCAP changes

1. The current Standard and Enterprise plans VCAP Services json file is different from that of the legacy plans. Any of your applications that consume the legacy plan VCAP Services json file must be changed to handle the current Standard and Enterprise plan json file. 
 
   For more information about the Standard and Enterprise VCAP Services json file, see [Connectivity options](https://cloud.ibm.com/docs/Db2onCloud?topic=Db2onCloud-connect_options)

### Console Changes

1. Console management differences (including IAM only access to certain features)

For more informations on User management and Roles visit: https://cloud.ibm.com/docs/Db2onCloud?topic=Db2onCloud-user_mgmt

### Db2 Changes

1. Standard and Enterprise plans do not run with the `DB2_WORKLOAD=ANALYTICS` registry parameter, hence the behavior of the COUNT aggregate function has changed. COUNT now returns an **INTEGER**, not a DECIMAL value. For more information, see [COUNT aggregate function](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.sql.ref.doc/doc/r0000759.html)