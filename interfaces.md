---

copyright:
  years: 2014, 2020
lastupdated: "2020-02-03"

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

# Interfaces
{: #interfaces}

You can work with your warehouse database in the following ways:
{: shortdesc}

   * From the web console
   * REST API
   * Connect applications or your favorite tools from your local computer
   * Use {{site.data.keyword.Db2_on_Cloud_short}} as a data source for your {{site.data.keyword.Bluemix_notm}} apps or services

## Web console
{: #web_console}

The web console provides a graphical interface for everything that you need to use your database, including: load facilities, an SQL editor, driver downloads, and more.
{: shortdesc}

<!-- ![View of the web console dashboard page](images/uc.png "Web console opens to the dashboard page"){: caption="Figure 1. View of the web console dashboard page" caption-side="bottom"} -->

<!-- Click the link to take a tour of the {{site.data.keyword.Db2_on_Cloud_short}} for Analytics web console: [General tour](http://ibm.biz/dashdb-general-quick-tour){:external}. -->

You can access your web console in the following ways:
   * From your {{site.data.keyword.Bluemix_notm}} dashboard - You can open the web console from the Service Details page for your {{site.data.keyword.Db2_on_Cloud_short}} service.
   * Direct URL - You can bookmark the URL of the web console for your {{site.data.keyword.Db2_on_Cloud_short}} service.

## REST API
{: #int_api}

With {{site.data.keyword.Db2_on_Cloud_short}} service plans, you can do tasks that are related to file management, loading data, and resource scaling by using one of the following REST APIs:
- [Database management API (Legacy)](https://cloud.ibm.com/apidocs/db2-on-cloud){:external}
- [Database management API (Standard and Enterprise)](https://cloud.ibm.com/apidocs/db2-on-cloud/db2-on-cloud-v4){: external}
- [Database resource scaling API](https://cloud.ibm.com/apidocs/db2-on-cloud/db2oc_scale_exp){:external}

## Connect applications or your favorite tools from your local computer
{: #connect_apps}

Configure your local environment to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database by completing the following steps:
{: shortdesc}

1. Download the [driver package](/docs/Db2onCloud/connecting?topic=Db2onCloud-drvr_pkg) from the {{site.data.keyword.Db2_on_Cloud_short}} web console.
2. Install the driver package on the computer where your apps or tools are running:
   - [Installing on Linux or PowerLinux](/docs/Db2onCloud/connecting?topic=Db2onCloud-drvr_pkg#drvr_install_linux)
   - [Installing on Mac OS X](/docs/Db2onCloud/connecting?topic=Db2onCloud-drvr_pkg#drvr_install_mac)
   - [Installing on Windows](/docs/Db2onCloud/connecting?topic=Db2onCloud-drvr_pkg#drvr_install_windows)
3. [Configure the driver files](/docs/Db2onCloud/connecting?topic=Db2onCloud-drvr_pkg#drvr_cfg_loc_env) for your {{site.data.keyword.Db2_on_Cloud_short}} database.

## Use Db2 Warehouse on Cloud as a data source for your {{site.data.keyword.Bluemix_notm}} apps or services
{: #data_src}

Apps that are hosted on {{site.data.keyword.Bluemix_notm}} can connect to your {{site.data.keyword.Db2_on_Cloud_short}} database the same way as your local applications connect to your {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

When your apps use the {{site.data.keyword.Bluemix_notm}} platform, you can take advantage of the `VCAP _SERVICES` environment variable to simplify the task of specifying database details and credentials:
1. On your {{site.data.keyword.Bluemix_notm}} dashboard, in the **Connections** tab of the Service Details page for your {{site.data.keyword.Db2_on_Cloud_short}} service, click the **Create connection** button.
2. Select the {{site.data.keyword.cloud_notm}} app to use with your {{site.data.keyword.Db2_on_Cloud_short}} database as a data source, and then click the **Connect** button.
3. Update your application code to retrieve database details and credentials from the `VCAP_SERVICES` environment variable:

    **Example without `VCAP_SERVICES`**

    ```php
    <?php
    $driver      = "DRIVER={IBM DB2 ODBC DRIVER};";

    $database    = "BLUDB";         # Get these database details from
    $hostname    = "<Host-name>";   # the Connection info page of the
    $port        = 50001;           # web console.
    $user        = "<User-ID >";    #
    $password    = "<Password>";    #
    $dsn         = "DATABASE=$database;" .
                   "HOSTNAME=$hostname;" .
                   "PORT=$port;" .
                   "PROTOCOL=TCPIP;" .
                   "UID=$user;" .
                   "PWD=$password;";

    $conn_string = $driver . $dsn;

    $conn        = db2_connect( $conn_string, "", "" );
    ?>
    ```

    **Example with `VCAP_SERVICES`**

    ```php
    <?php
    $driver      = "DRIVER={IBM DB2 ODBC DRIVER};";

    $vcap        = json_decode( getenv( "VCAP_SERVICES" ), true );
    $dsn         = $vcap[ "dashDB" ][0][ "credentials" ][ "dsn" ];

    $conn_string = $driver . $dsn;
                                   
    $conn        = db2_connect( $conn_string, "", "" );
    ?>
    ```

