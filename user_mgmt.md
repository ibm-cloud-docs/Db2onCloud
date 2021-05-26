---

copyright:
  years: 2014, 2020
lastupdated: "2020-10-30"

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

# Managing users
{: #user_mgmt}

## Current plans
{: #um_current_plans}

Access to {{site.data.keyword.Db2_on_Cloud_long}} service instances for users in your account is controlled by [Identity and access management (IAM) on IBM Cloud](/docs/Db2onCloud?topic=Db2onCloud-iam) and database access is provided by standard access controls provided by the database. 

For more information about IAM, see [What is IBM Cloud Identity and Access Management?](/docs/account?topic=account-iamoverview).

### User types
{: #um_user_types}

#### Database users
{: #um_db_users}

These are the users that are used to access the database. Traditionally, these are the OS users in a typical Db2 deployment, although, in the cloud, a user registry is used. Db2 understands these users as native to the database. The database privileges for the users can be granted or revoked as can roles that are created by the user. 

Database users are not granted any service-level functions. For example, a database administrator who has access to the data does not have the ability to change the configuration of the system outside of the database privileges that they were given.  

#### IAM users
{: #um_iam_users}

IAM is only integrated with high-level service access, which governs privileges and operations available in the {{site.data.keyword.Db2_on_Cloud_short}} console and database. Access to the database by these IAM users is provided by allowing an IAM user or service ID access to a specific Db2 user, as mentioned earlier.

### Roles and access
{: #um_roles_access}

Users can use JDBC or any Db2 client to connect to their database. There are two ways that users can access the database: 
- Use their database user name and password associated with their account 
- Use the IAM token (or APIKey, which gets the token) that is mapped to the associated database user 

IAM authentication is performed as the authentication mechanism. Permissions are not controlled by IAM. Permissions are controlled by database level privileges of the associated user. 

#### Console access
{: #um_console_access}

Console access is controlled by IAM. An IAM user can be assigned access by the IAM interface to all Db2 service instances, all Db2 service instances in a resource group, or a specific service instance. Within these parameters, IAM users can be assigned platform and service-level access.


| Role         | User mgmt | SQL editor/tables | Monitoring info | Settings (includes scale, backup, DR, etc.) | Info panels |
|--------------|-----------|-------------------|-----------------|-----------------------------------------|-------------|
| IAM - Platform - Viewer       | No | No (unless mapped to Db2 user) | Yes | No  | Yes |
| IAM - Platform - Operator     | No | No (unless mapped to Db2 user) | Yes | Yes | Yes |
| IAM - Platform - Editor       | No | No (unless mapped to Db2 user) | Yes | Yes | Yes |
| IAM - Platform - Administrator | Yes | No (unless mapped to Db2 user) | Yes | Yes | Yes |
| Non-IAM, but autheticate with JDBC | Only "Change password" | Yes | No | No | Yes |
{: caption="Table 1. Roles and console permissions" caption-side="top"}

#### Service action mapping
{: @um_serv_act_map}

Service action access is also controlled by IAM Roles. An IAM user can be assigned access by the IAM interface to all Db2 service instances, all Db2 service instances in a resource group, or a specific service instance. Within these parameters, IAM users can be assigned or revoked access from specific service actions.

| Role                          | Manage-users | Scale | Restore | DR |Settings | Backup | Monitor | View settings |
|-------------------------------|--------------|-------|---------|----|------|--------|---------|---------------|
| IAM - Platform - Viewer       | No           |  No   | No      | No |  No    | No     |  Yes    | Yes           |
| IAM - Platform - Operator     | No           |  Yes  | Yes     | Yes | Yes     | Yes    |  Yes    | Yes           |
| IAM - Platform - Editor       | No           |  Yes  | Yes     | Yes  | Yes     | Yes    |  Yes    | Yes           |
| IAM - Platform - Administrator | Yes          |  Yes  | Yes     | Yes | Yes     | Yes    |  Yes    | Yes           |
{: caption="Table 2. Roles and service actions" caption-side="top"} 

## Legacy plans
{: #um_legacy_plans}

Management of users that were given access to the database is the sole responsibility of the user or users with the administrator role. The administrator has the responsibility to manage how other users in your organization access your database.
{: shortdesc}

The database administrator role manages the following types of user access: 
* Web console. From the web console, users can run queries against the database.
* Database. The administrator can grant granular access permissions to the database, including being able to access only certain tables, schemas, or even rows or columns. 

For more information about user management, see [Database user management](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.security.doc/doc/user_mgmnt.html){:external}
