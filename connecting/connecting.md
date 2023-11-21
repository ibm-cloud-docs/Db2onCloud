---

copyright:
  years: 2014, 2020
lastupdated: "2020-11-10"

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

# Connecting overview
{: #connect_ov}

You can connect command-line interfaces, IBM® or third-party applications and tools, or apps that you create to your {{site.data.keyword.Db2_on_Cloud_short}} database. 
{: shortdesc}

## Prerequisites
{: #prereqs}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the prerequisites. 

- Collect database details and credentials

   To connect to your database, you need database details (such as the host name), and credentials (such as a user ID and password.) You can collect this connection information from the **Service credentials** table of the {{site.data.keyword.Db2_on_Cloud_short}} service instance or from the {{site.data.keyword.Db2_on_Cloud_short}} web console.

- Verify that a supported driver is installed

   - If your application or tool already contains the Db2 v11.5 IBM Data Server Driver Package, then your application or tool is able to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database by using that driver.
   - Otherwise, install the Db2 driver package, which you can download from [here](https://www.ibm.com/support/pages/node/387577){: external}.

- Configure your environment

  - Add entries to the driver configuration file, `db2dsdriver.cfg`, for your database.
  - Secure Sockets Layer (SSL)

    <!--Connection details, such as which port to use and the connection string, depend on whether you use SSL connections. For Enterprise and Standard plans, SSL is the default connection method. For legacy plans, using SSL is strongly recommended because of the stronger security it provides.

    <!-- You can choose to connect with or without SSL. Connection details, such as which port to use and the connection string, depend on whether you use SSL connections. -->

    To use SSL connections, you need a CA certificate:
    - If you use the most recent {{site.data.keyword.Db2_on_Cloud_short}} driver package, the certificate file is bundled with the package and is used for connections.
    - If you use the IBM Data Server Driver Package, you can download the SSL certificate from the {{site.data.keyword.Db2_on_Cloud_short}} web console.

- Confirm that ports are available

   If your network is behind a firewall, confirm that communications are permitted on the port that is needed to connect to the {{site.data.keyword.Db2_on_Cloud_short}} service. For Enterprise and Standard plans, the port number can be found in the connection information from the **Service credentials** table of the {{site.data.keyword.Db2_on_Cloud_short}} service instance or from the {{site.data.keyword.Db2_on_Cloud_short}} web console.

<!-- Before you can connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you completed downloading and installing the necessary components on the prerequisites checklist: 

- [Prerequisites checklist](prereqs.html) -->

### Collecting connection information
{: #collect_info}

- [Database details and connection credentials](/docs/Db2onCloud/connecting?topic=Db2onCloud-db_details_cxn_creds)

### Downloading and installing driver package
{: #dl_install}

- [Download driver package](/docs/Db2onCloud/connecting?topic=Db2onCloud-drvr_pkg)
- [Installing on Linux or PowerLinux](/docs/Db2onCloud/connecting?topic=Db2onCloud-drvr_pkg#drvr_install_linux)
- [Installing on Mac OS X](/docs/Db2onCloud/connecting?topic=Db2onCloud-drvr_pkg#drvr_install_mac)
- [Installing on Windows](/docs/Db2onCloud/connecting?topic=Db2onCloud-drvr_pkg#drvr_install_windows)

### Configuring your environment
{: #cfg_env}

- [Configuring your environment](/docs/Db2onCloud/connecting?topic=Db2onCloud-drvr_pkg#drvr_cfg_loc_env)
- [SSL connectivity](/docs/Db2onCloud/connecting?topic=Db2onCloud-ssl_support)

## Connectivity options
{: #connect_opts}

{{site.data.keyword.Db2_on_Cloud_short}} offers multiple secure connectivity options depending on your application connection requirements.  
{: shortdesc}

See [Connectivity options](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_options).

## Connecting programmatically
{: #conx_prgrm}

You can use common programming languages to create applications that connect to a {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

- [JDBC](/docs/Db2onCloud/connecting?topic=Db2onCloud-con_program#con_prog_jdbc)
- [Microsoft Windows ODBC or CLI](/docs/Db2onCloud/connecting?topic=Db2onCloud-con_program#con_prog_odbc_cli)
- [.NET](/docs/Db2onCloud/connecting?topic=Db2onCloud-con_program#con_prog_net)
- [ODBC Data Source Administrator](/docs/Db2onCloud/connecting?topic=Db2onCloud-con_program#con_prog_odbc_dsa)
- [PHP](/docs/Db2onCloud/connecting?topic=Db2onCloud-con_program#con_prog_php)
- [REST API](/docs/Db2onCloud/connecting?topic=Db2onCloud-con_rest_api)
<!-- - [C++]() -->
<!-- - [Java]() -->
<!-- - [Node.js]() -->
<!-- - [Perl]() -->
<!-- - [Python]() -->

## Integrating apps and tools
{: #conx_apps_tools}

You can also connect external applications and tools to {{site.data.keyword.Db2_on_Cloud_short}} and use them to further manage or analyze your data. For example:

### Data integration
{: #di}

- Connect your {{site.data.keyword.Bluemix_short}} applications that need an analytics database.
- [DataStage](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ibm#datastage)
<!-- - [Informatica](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_3rd_party#informatica) -->
- [InfoSphere Data Replication](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ibm#idr)
- [Segment](https://segment.com/docs/destinations/db2/){:external}
- [Data Studio](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ibm#data_studio)
- [Data Server Manager](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ibm#dsm)
- [CLPPLUS](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ibm#clpplus)
<!-- - [Aginity Workbench to migrate Netezza® data models and data to {{site.data.keyword.Db2_on_Cloud_short}}](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_3rd_party#aginity_wb) -->
- [InfoSphere Data Architect to design and deploy your database schema](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ibm#ida)

### Data visualization & BI
{: #dvis_bi}

<!-- - [Cognos Analytics to run Business Intelligence reports against your data](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ibm#cognos) -->
- [Looker](https://docs.looker.com/setup-and-management/connecting-to-db){:external}
- [Tableau](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_3rd_party#tableau)
- [Microsoft Excel](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_3rd_party#excel)
<!-- - [Esri ArcGIS for Desktop to perform geospatial analytics and map publishing with your data](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_3rd_party#esri_arcgis) -->

### Data science
{: #dsci}

- [Watson Studio (formerly IBM Data Science Experience)](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ibm#watson_studio)
- [SPSS Statistics](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ibm#spss_stats)
- [SAS](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_3rd_party#sas)
<!-- - [Local R development environment](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_3rd_party#r_dev_env) -->

## Connecting to another Db2 database
{: #fed}

Db2 data virtualization (also known as federation) is supported by {{site.data.keyword.Db2_on_Cloud_short}}. Data virtualization gives you single-query access to all of your data that is on multiple distributed databases anywhere in your organization. You can access data that is on any of your Db2 or Informix data sources, both in the cloud and on premises. 

This function is supported on all versions of {{site.data.keyword.Db2_on_Cloud_short}}, except for the free Lite plan. However, you can use the Lite plan as a target from which you can pull data.

- [Data virtualization (federation)](/docs/Db2onCloud?topic=Db2onCloud-fed_v2)


