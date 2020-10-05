---

copyright:
  years: 2014, 2019
lastupdated: "2019-12-18"

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

# Database details and connection credentials
{: #db_details_cxn_creds}

To configure your local development environment and to connect applications and tools to your {{site.data.keyword.Db2_on_Cloud_short}} database, you need to know the database details and connection credentials.
{: shortdesc}

## Database details
{: #db_details}

There are important database details that are needed for connecting applications and tools to your database:

- *Host name* - The host name of the server.
- *Port number* - Used by the database manager for TCP/IP communication. (Note that your service is provisioned with connections that use Secure Socket Layer (SSL))

   If needed, you can get the IP address of your server by using the ping command or the nslookup command, specifying your host name.
- *Database name* - The Db2 database name, usually BLUDB.

## Connection credentials
{: #cxn_creds}

There are three types of credentials:

- *IBMid* - If you use {{site.data.keyword.Bluemix_notm}}, this is the ID you would use to log in to {{site.data.keyword.Bluemix_notm}}. On the IBMID can be used to manage users by accessing User Management in the Console.  This is not what you use to connect applications or tools to your {{site.data.keyword.Db2_on_Cloud_short}} database. 
- *Db2 database credentials* - These credentials are generated when you create New Credentials under Service Credentials for the Service in IBM Cloud.
- *IBMid-created users* - These IBMid-created user IDs and passwords can be used to log directly into the web console URL and to connect to the Db2 database from applications or tools.

## Where to find database details and connection credentials
{: #location}

You can collect this information from the following places:

- *The Service Owner* - If you are not the owner of your Db2 instance, you can get your database details and connect credentials from the owner.
- *Db2 web console* - Database details and credentials are available in the web console.
- If you are using {{site.data.keyword.Bluemix_notm}}: 
   
   - *{{site.data.keyword.Bluemix_notm}} Dashboard* - When you view your service on your {{site.data.keyword.Bluemix_notm}} dashboard, you can view the database details, the database user ID, and password. To retrieve your service credentials, select the **Service credentials** tab from your service page, click the **New credential** button, then select **View credentials**.
   - *`VCAP_SERVICES`* - `VCAP_SERVICES` is an environment variable in {{site.data.keyword.Bluemix_notm}} that contains database details and credentials in JSON format. When you view the service credentials for your service in your {{site.data.keyword.Bluemix_notm}} dashboard, the contents of `VCAP_SERVICES` is what is displayed. When you bind other {{site.data.keyword.Bluemix_notm}} services or apps to your service, those other services or apps can access database details and credentials programmatically by reading `VCAP_SERVICES`.
