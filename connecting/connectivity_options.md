---

copyright:
  years: 2014, 2020
lastupdated: "2020-02-14"

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

{{site.data.keyword.Db2_on_Cloud_long}} offers multiple secure connectivity options depending on your application connection requirements.  
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

Non-admin users can also use whitelisting available in the {{site.data.keyword.Db2_on_Cloud_short}} web console under **Settings > Manage Users**.

## Connecting to a private endpoint: IBM Cloud Service Endpoint
{: #priv_endpt}

If you have an application that is deployed on your {{site.data.keyword.cloud_notm}} account and want to connect it to your database without the database traffic to flow over any public networks, you can use the **{{site.data.keyword.cloud_notm}} Service Endpoint** option when ordering your database. You are provided with a private host name at the time that the service is provisioned and you can connect to it only from within your {{site.data.keyword.cloud_notm}} account.

Optional IP whitelisting is offered as well with this option. Create an IBM Support case if you want to enable IP whitelisting with CSE.

To learn more about the {{site.data.keyword.cloud_notm}} Service Endpoint option, see [Service Endpoint: About](/docs/service-endpoint?topic=service-endpoint-about#about).


### How to connect to a private endpoint with IBM Cloud Service Endpoint
{: #priv_endpt_steps}

Private network and endpoint communication happens by way of the {{site.data.keyword.cloud_notm}} Service Endpoint service. The Service Endpoint service makes it easy to quickly and securely route network traffic between different {{site.data.keyword.cloud_notm}} services and your database over the {{site.data.keyword.cloud_notm}} private network backplane. This network routing ensures that your data never goes out to the public internet. 

To get started with Service Endpoint, your {{site.data.keyword.cloud_notm}} account must be enabled for virtual routing and forwarding (VRF). To get your account enabled, see [Enabling your account for using Service Endpoint by using IBM Cloud CLI](/docs/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps).

After your account is VRF enabled and the Service Endpoint is enabled, follow the instructions that were provided in your welcome letter.

Now, it’s time to connect to your {{site.data.keyword.Db2_on_Cloud_short}} instance from within your {{site.data.keyword.cloud_notm}} account by way of the private network address that was provided in your welcome letter.

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
