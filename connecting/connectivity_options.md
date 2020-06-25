---

copyright:
  years: 2014, 2020
lastupdated: "2020-06-24"

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

# Connectivity options
{: #connect_options}

{{site.data.keyword.Db2_on_Cloud_long}} offers multiple secure connectivity options that depend on your application connection requirements.  
{: shortdesc}

## Connecting to a public endpoint (default option)
{: #pub_endpt}

As with any public cloud service, you can connect your application by way of a public host name that is provided to you at the time that your service is provisioned. Access to your data is protected by strong authentication, vast Db2 authorization options and access controls, encryption over the wire and at rest, and IBM security and compliance practices for development and operations. 

### How to connect to a public endpoint:
{: #pub_endpt_steps}

The easiest way to connect to your data is by way of the public host name that was provided in your welcome letter. You can also obtain your host name and credentials in the following way:

1. Log in to {{site.data.keyword.Db2_on_Cloud_short}} and click your service instance.
2. Click **Service credentials**.
3. Click **New credential**, then click **Add**.
4. After the credentials are created, under the `Actions` column, click **View credentials**.
5. In the following JSON document example, note the contents of the hostname, password, and username fields. You use these three components to make the public endpoint connection:

#### Current plans connection string breakdown
{: #pub_endpt_current}

##### Db2 on Cloud section

The "postgres" section contains information that is suited to applications that make connections to {{site.data.keyword.Db2_on_Cloud_short}}.

| Field Name | Index | Description |
|----------|--------|-----------|
| `Type` | | Type of connection - "URI" |
| `Scheme` | | Scheme for a URI - "{{site.data.keyword.Db2_on_Cloud_short}}" |
| `Path` | | Path for a URI - Database name. The default is `ibmclouddb`. |
| `Authentication` | `Username` | The user name that you use to connect |
| `Authentication` | `Password` | A password for the user - might be shown as `$PASSWORD` |
| `Authentication` | `Method` | How authentication takes place; "direct" authentication is handled by the driver |
| `Hosts` | `0...` | A host name and port to connect to |
| `Composed` | `0...` | A URI combining Scheme, Authentication, Host, and Path |
| `Certificate` | `Name` | The allocated name for the self-signed certificate for database deployment |
| `Certificate` | Base64 | A base64 encoded version of the certificate |
| `Host_ROS` | | A host name and port to connect to read on standby |
{: caption="Table 1. Db2 on Cloud / URI connection information" caption-side="top"}

`0...` indicates that there might be one or more of these entries in an array.

##### CLI section

The "CLI" section contains information that is suited for connecting with `psql`.

| Field Name | Index | Description |
|----------|--------|-----------|
| `Bin` | | The recommended binary to create a connection; in this case it is `psql` |
| `Composed` | | A formatted command to establish a connection to your deployment. The command combines the `Bin` executable, `Environment` variable settings, and uses `Arguments` as command line parameters. |
| `Environment` | | A list of key/values you set as environment variables |
| `Arguments` | `0...` | The information that is passed as arguments to the command shown in the Bin field |
| `Certificate` | Base64 | A self-signed certificate that is used to confirm that an application is connecting to the appropriate server. It is base64 encoded. |
| `Certificate` | Name | The allocated name for the self-signed certificate |
| `Type` | | The type of package that uses this connection information; in this case `cli` |
{: caption="Table 2. psql / cli connection information" caption-side="top"}

`0...` indicates that there might be one or more of these entries in an array.

#### Legacy plans
{: #pub_endpt_legacy}

   ```
   {
     "hostname": "dashdb-enterprise-xxxxxxx.services.dal.bluemix.net",
     "password": "DTPY7KXxhp_pKtjLSt",
     "https_url": "https://dashdb-enterprise-xxxxxxx.services.dal.bluemix.net",
     "port": 50000,
     "ssldsn": "DATABASE=BLUDB;HOSTNAME=dashdb-enterprise-xxxxxx.services.dal.bluemix.net;PORT=50001;PROTOCOL=TCPIP;UID=bluadmin;PWD=DTPY7KXWxhp_pKtjLSt;Security=SSL;",
     "host": "dashdb-enterprise-xxxxxxx.services.dal.bluemix.net",
     "jdbcurl": "jdbc:db2://dashdb-enterprise-xxxxxxx.services.dal.bluemix.net:50000/BLUDB",
     "uri": "db2://bluadmin:DTPY7KXx1p_pKtjLSt@dashdb-enterprise-xxxxxxx.services.dal.bluemix.net:50000/BLUDB",
     "db": "BLUDB",
     "dsn": "DATABASE=BLUDB;HOSTNAME=dashdb-enterprise-xxxxxxx.services.dal.bluemix.net;PORT=50000;PROTOCOL=TCPIP;UID=bluadmin;PWD=DTPYZunlWxhp_pKtjLSt;",
     "username": "bluadmin",
     "ssljdbcurl": "jdbc:db2://dashdb-enterprise-xxxxxxx.services.dal.bluemix.net:50001/BLUDB:sslConnection=true;"
   }

   ```

   ![Public network access to {{site.data.keyword.cloud_notm}}](images/public_connection.png "Graphical view of user to cloud connection"){: caption="Figure 1. Public network access to {{site.data.keyword.cloud_notm}}" caption-side="bottom"}

Non-admin users can also use allowlisting available in the {{site.data.keyword.Db2_on_Cloud_short}} web console under **Settings > Manage Users**.

## Connecting to a private endpoint: IBM Cloud service endpoint
{: #priv_endpt}

{{site.data.keyword.Db2_on_Cloud_short}} supports private connectivity through an [{{site.data.keyword.cloud_notm}} service endpoint](/docs/resources?topic=resources-service-endpoints). {{site.data.keyword.cloud_notm}} service endpoints securely route network traffic between different {{site.data.keyword.cloud_notm}} services through the {{site.data.keyword.cloud_notm}} private backplane network. When you configure your {{site.data.keyword.Db2_on_Cloud_short}} instance with {{site.data.keyword.cloud_notm}} service endpoint connectivity, traffic between your cloud database and applications deployed on your {{site.data.keyword.cloud_notm}} account will not traverse any public networks.

### How to configure IBM Cloud service endpoint connectivity
{: #cfg_endpt}

Complete the following steps to enable {{site.data.keyword.cloud_notm}} service endpoint connectivity for your {{site.data.keyword.Db2_on_Cloud_short}} instance:

1. Enable your {{site.data.keyword.cloud_notm}} account to use virtual routing and forwarding (VRF) and {{site.data.keyword.cloud_notm}} service endpoints. To enable both of these items, see [Setting up service endpoints](/docs/resources?topic=resources-private-network-endpoints).

2. Configure your {{site.data.keyword.Db2_on_Cloud_short}} instance for service endpoint connectivity.

   - **If you provisioned your {{site.data.keyword.Db2_on_Cloud_short}} instance through the {{site.data.keyword.cloud_notm}} catalog**: [Create a case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external} to request the configuration of your {{site.data.keyword.Db2_on_Cloud_short}} instance for {{site.data.keyword.cloud_notm}} service endpoint connectivity. After this is complete, your {{site.data.keyword.Db2_on_Cloud_short}} instance will be served on a new, non-internet-routable IP address. Information about how to access your {{site.data.keyword.Db2_on_Cloud_short}} instance by using this newly configured private endpoint will be sent to you.

   - **If you purchased your {{site.data.keyword.Db2_on_Cloud_short}} instance through IBM Sales**: If you requested private endpoint connectivity, your {{site.data.keyword.Db2_on_Cloud_short}} instance will be provisioned with {{site.data.keyword.cloud_notm}} service endpoint connectivity. No further action is required.

After you've configured {{site.data.keyword.cloud_notm}} service endpoint connectivity for your {{site.data.keyword.Db2_on_Cloud_short}} instance, it will only be accessible through a private endpoint. You will not be able to access your instance through a public endpoint.
{: note}

To learn more about the {{site.data.keyword.cloud_notm}} service endpoint service, see [Secure access to services using service endpoints](/docs/resources?topic=resources-service-endpoints).

<!--
## Connecting to a private endpoint: IBM Cloud Service Endpoint
{: #priv_endpt}

If you have an application that is deployed on your {{site.data.keyword.cloud_notm}} account and want to connect it to your database without the database traffic to flow over any public networks, you can use the **{{site.data.keyword.cloud_notm}} Service Endpoint** option when ordering your database. You are provided with a private host name at the time that the service is provisioned and you can connect to it only from within your {{site.data.keyword.cloud_notm}} account.

Optional IP whitelisting is offered as well with this option. Create an [IBM Support case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external} if you want to enable IP whitelisting with CSE.

To learn more about the {{site.data.keyword.cloud_notm}} Service Endpoint option, see [Secure access to services using service endpoints](/docs/resources?topic=resources-service-endpoints).


### How to connect to a private endpoint with IBM Cloud Service Endpoint
{: #priv_endpt_steps}

Private network and endpoint communication happens by way of the {{site.data.keyword.cloud_notm}} Service Endpoint service. The Service Endpoint service makes it easy to quickly and securely route network traffic between different {{site.data.keyword.cloud_notm}} services and your database over the {{site.data.keyword.cloud_notm}} private network backplane. This network routing ensures that your data never goes out to the public internet. 

To get started with Service Endpoint, your {{site.data.keyword.cloud_notm}} account must be enabled for virtual routing and forwarding (VRF). To get your account enabled, see [Setting up service endpoints](/docs/resources?topic=resources-private-network-endpoints).

After your account is VRF enabled and the Service Endpoint is enabled, follow the instructions that were provided in your welcome letter.

Now, it’s time to connect to your {{site.data.keyword.Db2_on_Cloud_short}} instance from within your {{site.data.keyword.cloud_notm}} account by way of the private network address that was provided in your welcome letter.
-->

## Connecting to a virtual private network (VPN) endpoint
{: #vpn}

If you have an application that is deployed on a private network that is outside of the {{site.data.keyword.cloud_notm}} without access to the public internet and you want to connect it to your database over a virtual private network (VPN) connection, you can make the request at the time that you order the service or by opening an IBM Support case. IBM network engineers will assist your network engineers to set up the VPN tunnel between your private network and the {{site.data.keyword.cloud_notm}}.

### How to connect to a VPN endpoint
{: #priv_endpt_vpn_steps}

To establish a VPN connection to your cloud database behind a public endpoint, [create an {{site.data.keyword.cloud_notm}} Support case](https://cloud.ibm.com/unifiedsupport/cases/add){:external} that includes the following details:

* **Type of support**: Technical 
* **Category**: Databases 
* **Offering**: select your {{site.data.keyword.Db2_on_Cloud_short}} instance 
* **Subject**: VPN Connection Request 
* **Description**: provide the following required information
  * **Customer-side VPN Peer Address** (your VPN endpoint): `<IP Address>`
  * **Customer-side Encryption Domain** (be specific about what is required – 10.0.0.0/8 is unworkable because 10 addressing is also used within the {{site.data.keyword.cloud_notm}} for back-end services): `<Domain>`
  * **Customer-side VPN Hardware & Version**: `<Hardware and Version number>`
  * **Customer-side VPN Contact** (technical contact name and email address): 
    * `<Name>` 
    * `<Title>` 
    * `<Email Address>`

  **Optional** (change only if the following default values are not suitable):

  *IKE/ISAKMP Parameters (Phase I)*

  * **Encryption Method**: IKEv1
  * **IKE Encryption / Encryption Algorithm**: AES-256
  * **Authentication Algorithm**: SHA1
  * **DH-Group**: Group 5
  * **Security Association Lifetime (seconds)**: 1d (86400 seconds)

  *IPSec Parameters (Phase II)*

  * **IPSec Encryption / Encryption Algorithm**: AES-256
  * **Authentication Algorithm**: SHA1
  * **DH-Group** (if using PF-Secrecy): Group 5
  * **Security Association Lifetime (seconds)**: 3600 seconds

After receipt of your request, {{site.data.keyword.cloud_notm}} technicians will open the appropriate firewall ports and whitelist the provided IP address. Communication and resolution to the request will be made through the {{site.data.keyword.cloud_notm}} Support case ticket.

![Public network access to {{site.data.keyword.cloud_notm}} through a VPN](images/public_connection_vpn.png "Graphical view of user to cloud connection"){: caption="Figure 2. Public network access to {{site.data.keyword.cloud_notm}} through a VPN" caption-side="bottom"}
