---

copyright:
  years: 2014, 2020
lastupdated: "2020-11-18"

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

**We recommend using Hostnames and not IP Addresses, since the underlying IP address may change**

You can obtain your hostname, port and credentials in the following ways:

#### From the console
{: #pub_console}

1. Log in to {{site.data.keyword.Db2_on_Cloud_short}} and click your service instance.
2. Click **Manage**.
3. Click **Open Console**, then click **Administration**.
4. Select **Connections**.
5. The public and private endpoints will be displayed under **Connection Configuration Resources** by selecting the respective radio button.

#### From service credentials
{: #pub_sc}

1. Log in to {{site.data.keyword.Db2_on_Cloud_short}} and click your service instance.
2. Click **Service credentials**.
3. Click **New credential**, then click **Add**.
4. After the credentials are created, click the down arrow beside the credential names to view the credentials.
5. In the following JSON document example, note the contents of the hostname, port, password, and username fields. You use these four components to make the public endpoint connection:

#### Current plans connection string breakdown
{: #pub_endpt_current}

##### Db2 on Cloud section
{: #pub_db2oc}

The "db2" section contains information that is suited to applications that make connections to {{site.data.keyword.Db2_on_Cloud_short}}.

| Field Name | Index | Description |
|----------|--------|-----------|
| `Type` | | Type of connection - "URI" |
| `Scheme` | | Scheme for a URI - "db2" |
| `Path` | | Path for a URI - Database name. The default is `bludb`. |
| `Authentication` | `Username` | The user name that you use to connect |
| `Authentication` | `Password` | A password for the user |
| `Authentication` | `Method` | How authentication takes place; "direct" authentication is handled by the driver |
| `Hosts` | `0...` | A host name and port to connect to |
| `Composed` | `0...` | A URI combining Scheme, Authentication, Host, and Path |
| `Certificate` | `Name` | The allocated name for the self-signed certificate for database deployment |
| `Certificate` | Base64 | A base64 encoded version of the certificate |
| `Host_ROS` | | A host name and port to connect to read on standby |
{: caption="Table 1. Db2 on Cloud / URI connection information" caption-side="top"}

`0...` indicates that there might be one or more of these entries in an array.

##### CLI section
{: #pub_cli}

The "cli" section contains information that is suited for connecting with `db2`.

| Field Name | Index | Description |
|----------|--------|-----------|
| `Bin` | | The recommended binary to create a connection; in this case it is `db2` |
| `Composed` | | A formatted command to establish a connection to your deployment. The command combines the `Bin` executable, `Environment` variable settings, and uses `Arguments` as command line parameters. |
| `Environment` | | A list of key/values you set as environment variables |
| `Arguments` | `0...` | The information that is passed as arguments to the command shown in the Bin field |
| `Certificate` | Base64 | A self-signed certificate that is used to confirm that an application is connecting to the appropriate server. It is base64 encoded. |
| `Certificate` | Name | The allocated name for the self-signed certificate |
| `Type` | | The type of package that uses this connection information; in this case `cli` |
{: caption="Table 2. psql / cli connection information" caption-side="top"}

`0...` indicates that there might be one or more of these entries in an array.

#### Enterprise and Standard plans
{: #pub_endpt_ent_stand}

The following VCAP Services json file can be used to make connections to your Enterprise and Standard plans database instances:

```
{
  "apikey": "<apikey>",
  "connection": {
    "cli": {
      "arguments": [
        [
          "-u",
          "ipa8emxc",
          "-p",
          "e2haTt1FJ7m3UQXY",
          "--ssl",
          "--sslCAFile",
          "2ac5a4d3-1307-40f5-99a4-043e278fb084",
          "--authenticationDatabase",
          "admin",
          "--host",
          "a1d53ce7-166c-42d1-af26-7809dexxxxxx.yyyyyy.databases.appdomain.cloud:32447"
        ]
      ],
      "bin": "db2",
      "certificate": {
        "certificate_base64": "<certificate_code>",
        "name": "2ac5a4d3-1307-40f5-99a4-043e278fb084"
      },
      "composed": [
        "db2 -u ipa8emxc -p e2haTt1FJ7m3UQXY --ssl --sslCAFile 2ac5a4d3-1307-40f5-99a4-043e278fb084 --authenticationDatabase admin --host a1d53ce7-166c-42d1-af26-7809dexxxxxx.yyyyyy.databases.appdomain.cloud:32447"
      ],
      "environment": {},
      "type": "cli"
    },
    "db2": {
      "authentication": {
        "method": "direct",
        "password": "<password>",
        "username": "<user_name>"
      },
      "certificate": {
        "certificate_base64": "<certificate_code>",
        "name": "2ac5a4d3-1307-40f5-99a4-043e278fb084"
      },
      "composed": [
        "db2://ipa8emxc:e2haTt1FJ7m3UQXY@a1d53ce7-166c-42d1-af26-7809dexxxxxx.yyyyyy.databases.appdomain.cloud:32447/bludb?authSource=admin&replicaSet=replset"
      ],
      "database": "bludb",
      "host_ros": [
        "a1d53ce7-166c-42d1-af26-7809dexxxxxx.yyyyyy.databases.appdomain.cloud:31196"
      ],
      "hosts": [
        {
          "hostname": "a1d53ce7-166c-42d1-af26-7809dexxxxxx.yyyyyy.databases.appdomain.cloud",
          "port": 32447
        }
      ],
      "jdbc_url": [
        "jdbc:db2://a1d53ce7-166c-42d1-af26-7809dexxxxxx.yyyyyy.databases.appdomain.cloud:32447/bludb:user=<userid>;password=<your_password>;sslConnection=true;"
      ],
      "path": "/bludb",
      "query_options": {
        "authSource": "admin",
        "replicaSet": "replset"
      },
      "replica_set": "replset",
      "scheme": "db2",
      "type": "uri"
    }
  },
}
```

#### Legacy plans
{: #pub_endpt_legacy}

The following VCAP Services json file can be used to make connections to your legacy plan database instances:

```
{
  "hostname": "dashdb-enterprise-xxxxxxx.services.dal.bluemix.net",
  "password": "<password>",
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

{{site.data.keyword.Db2_on_Cloud_short}} supports private connectivity through an [{{site.data.keyword.cloud_notm}} service endpoint](/docs/account?topic=account-service-endpoints-overview). {{site.data.keyword.cloud_notm}} service endpoints securely route network traffic between different {{site.data.keyword.cloud_notm}} services through the {{site.data.keyword.cloud_notm}} private backplane network. When you configure your {{site.data.keyword.Db2_on_Cloud_short}} instance with {{site.data.keyword.cloud_notm}} service endpoint connectivity, traffic between your cloud database and applications deployed on your {{site.data.keyword.cloud_notm}} account will not traverse any public networks.

### How to configure IBM Cloud private endpoint connectivity
{: #cfg_priv_endpt}

Complete the following steps to enable {{site.data.keyword.cloud_notm}} private endpoint connectivity for your {{site.data.keyword.Db2_on_Cloud_short}} instance:

Enable your {{site.data.keyword.cloud_notm}} account to use virtual routing and forwarding (VRF) and {{site.data.keyword.cloud_notm}} service endpoints. To enable both of these items, see [Enabling VRF and service endpoints](/docs/account?topic=account-vrf-service-endpoint).

- For Enterprise and Standard plans
  1. On the console, click **Administration**.
  2. Click **Access restriction**.
  3. Select **Private endpoints** or **Public-and-private endpoints** and click **Update** to enable private endpoints.

     ![Configuring private endpionts {{site.data.keyword.cloud_notm}}](images/private_endpoints.png "Graphical view of configuring private end points"){: caption="Figure 2. Configuring private endpoints on {{site.data.keyword.Db2_on_Cloud_long}}" caption-side="bottom"}

- For Legacy plans

  Configure your {{site.data.keyword.Db2_on_Cloud_short}} instance for private endpoint connectivity.

  - **If you provisioned your {{site.data.keyword.Db2_on_Cloud_short}} instance through the {{site.data.keyword.cloud_notm}} catalog**: [Create a case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external} to request the configuration of your {{site.data.keyword.Db2_on_Cloud_short}} instance for {{site.data.keyword.cloud_notm}} service endpoint connectivity. After this is complete, your {{site.data.keyword.Db2_on_Cloud_short}} instance will be served on a new, non-internet-routable IP address. Information about how to access your {{site.data.keyword.Db2_on_Cloud_short}} instance by using this newly configured private endpoint will be sent to you.

  - **If you purchased your {{site.data.keyword.Db2_on_Cloud_short}} instance through IBM Sales**: If you requested private endpoint connectivity, your {{site.data.keyword.Db2_on_Cloud_short}} instance will be provisioned with {{site.data.keyword.cloud_notm}} service endpoint connectivity. No further action is required.

After you've configured {{site.data.keyword.cloud_notm}} private endpoint connectivity for your {{site.data.keyword.Db2_on_Cloud_short}} instance, it will only be accessible through a private endpoint. You will not be able to access your instance through a public endpoint.
{: note}

To learn more about the {{site.data.keyword.cloud_notm}} endpoint service, see [Secure access to services using service endpoints](/docs/account?topic=account-service-endpoints-overview).

## Connecting to a virtual private network (VPN) endpoint
{: #priv_endpt_vpn}

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

After receipt of your request, {{site.data.keyword.cloud_notm}} technicians will open the appropriate firewall ports and allowlist the provided IP address. Communication and resolution to the request will be made through the {{site.data.keyword.cloud_notm}} Support case ticket.

![Public network access to {{site.data.keyword.cloud_notm}} through a VPN](images/public_connection_vpn.png "Graphical view of user to cloud connection"){: caption="Figure 3. Public network access to {{site.data.keyword.cloud_notm}} through a VPN" caption-side="bottom"}
