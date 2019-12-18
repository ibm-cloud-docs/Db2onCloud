---

copyright:
  years: 2014, 2019
lastupdated: "2019-12-18"

keywords: 

subcollection: Db2onCloud

---

<!-- Attribute definitions --> 
{:javascript: #javascript .ph data-hd-programlang='javascript'}
{:java: #java .ph data-hd-programlang='java'}
{:ruby: #ruby .ph data-hd-programlang='ruby'}
{:php: #php .ph data-hd-programlang='php'}
{:python: #python .ph data-hd-programlang='python'}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# Getting started with {{site.data.keyword.Db2_on_Cloud_short}}
{: #getting-started}

{{site.data.keyword.Db2_on_Cloud_long}} is an SQL database that is provisioned for you in the cloud. You can use {{site.data.keyword.Db2_on_Cloud_short}} just as you would use any database software, but without the time and expense of hardware setup or software installation and maintenance. 
{: shortdesc}

Create credentials. For those of you new to IBM Cloud and after creating the service, you must create a user name and password by clicking the **Create Credentials** button when you start the service. Technically, you can log in to the web console without credentials, but you need the user name and password to use many of the Db2 tools. To retrieve existing credentials, select the **Service credentials** tab from your service page, click the **New credential** button, then select **View credentials**.
{: important}

You can also install a local Db2 database by using the [free Db2 Developer Edition download](https://www.ibm.com/us-en/marketplace/ibm-db2-direct-and-developer-editions){:external}. It rapidly installs a ready-to-go developer edition of Db2 with tools inside a Docker container (Docker not required; it automatically installs any necessary components). 

## Interfaces
{: #interfaces}

You can work with your {{site.data.keyword.Db2_on_Cloud_short}} database in the following ways:
{: shortdesc}

   * {{site.data.keyword.Db2_on_Cloud_short}} web console
   * REST API
   * Connect applications or your favorite tools from your local computer
   * Use {{site.data.keyword.Db2_on_Cloud_short}} as a data source for your {{site.data.keyword.Bluemix_notm}} apps or services

### Db2 on Cloud web console
{: #web_console}

The web console provides a graphical interface for everything that you need to use your database, including: load facilities, an SQL editor, driver downloads, and more.
{: shortdesc}

<!-- ![View of Db2 on Cloud web console dashboard page](images/console_v2.png) -->
<!-- ![View of {{site.data.keyword.dashdbshort_notm}} web console dashboard page](images/console_v2.jpg) -->

<!-- Click the link to take a tour of the Db2 web console: [General tour](http://ibm.biz/dashdb-general-quick-tour){:external}. -->

You can access your {{site.data.keyword.Db2_on_Cloud_short}} web console in the following ways:
   * From your {{site.data.keyword.Bluemix_notm}} dashboard - You can open the web console from the Service Details page for your {{site.data.keyword.Db2_on_Cloud_long_notm}} service.
   * Direct URL - You can bookmark the URL of the web console for your {{site.data.keyword.Db2_on_Cloud_short}} service.

<!-- ###REST APIs
{: #apis}

With Db2 Warehouse plans, you can perform tasks related to file management, loading data, and running R scripts by using the [Db2 Warehouse REST API](http://ibm.biz/dashdb-api){:external}.
{: shortdesc} -->

### Installing Db2 command-line clients and drivers on your computer
{: #connect_apps}

In most cases, users tend to use only the REST API, or install drivers for a framework, for example, with Python's `pip` command. 
{: shortdesc}

To install Python driver packages for the MacOS, you must use the `pip` command with the `--no-cache-dir` option. For detailed instructions, see: [Python support for IBM Db2 and IBM Informix](https://ibm.biz/db2-drivers-python){:external}
{: note}

If you are doing data science work with Python, or want support for data frames, in-database analytics, or by using Watson Studio, you might want to use the following alternative driver, which focuses on support for various data science functions: [ibmdbpy 0.1.5](https://pypi.org/project/ibmdbpy/){:external}.
{: note}

<!-- Drivers on site are broken so taking out this one -Simon. 1. Download the [driver package](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package.html){:external} from the Connection info page of the {{site.data.keyword.Db2_on_Cloud_short}} web console.-->

To install Python or Node.js framework drivers, click one of the following links:
- [Python drivers](https://ibm.biz/db2-drivers-python){:external}
- [Node.js drivers](https://ibm.biz/db2-drivers-node){:external}

To install the Node.js ORM called Sequelize, click the following link:
[Sequelize](https://github.com/ibmdb/sequelize){:external}
{: note}

For more driver installation options, including Java, Go, Jupyter Notebooks, Ruby, PHP, and more, click the following link: 

- [ibmdb](https://github.com/ibmdb){:external}

Assuming that you already installed framework drivers, you can skip the following steps. However, power users might want to use the Db2 command-line client to administer their database and use Db2 commands. Also, certain ODBC or JDBC applications can benefit from a general installation of Db2 drivers. If so, complete the following steps:

1. [Install the driver package](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_install.html){:external} on the computer where your apps or tools are running.
2. [Configure the driver files](https://www.ibm.com/support/knowledgecenter/en/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:external} for your {{site.data.keyword.Db2_on_Cloud_short}} database.

### Use Db2 on Cloud as a data source for your {{site.data.keyword.Bluemix_notm}} apps or services
{: #data_src}

Apps that are hosted on {{site.data.keyword.Bluemix_notm}} can connect to your {{site.data.keyword.Db2_on_Cloud_short}} database the same way that your local applications connect to your {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

When your apps use the {{site.data.keyword.Bluemix_notm}} platform, you can take advantage of the `VCAP _SERVICES` environment variable to simplify the task of specifying database details and credentials:
1. On your {{site.data.keyword.Bluemix_notm}} dashboard, in the **Connections** tab of the Service Details page for your {{site.data.keyword.Db2_on_Cloud_long_notm}} service, click the **Create connection** button.
2. Select the {{site.data.keyword.Bluemix_notm}} app to use with your {{site.data.keyword.Db2_on_Cloud_short}} database as a data source, and then click the **Connect** button.
3. Update your application code to retrieve database details and credentials from the `VCAP_SERVICES` environment variable:

    **Example without `VCAP_SERVICES`**

    ```php
    <?php
    $driver      = "DRIVER={IBM DB2 ODBC DRIVER};";

    $database    = "BLUDB";         # Get these database details from
    $hostname    = "<Host-name>";   # the Connect page of the Db2 on Cloud
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

## Samples
{: #samples}

Here are links to samples that demonstrate how to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database from applications in different languages:
{: shortdesc}

   * [.NET](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:external}
<!-- * [JAVA](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_java.html){:external} -->
   * [JDBC](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:external}
<!-- * [Node.js](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_nodejs.html){:external} -->
   * [PHP](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:external}
<!-- * [Python](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_python.html){:external} -->
<!-- * [{{site.data.keyword.Db2_on_Cloud_short}} samples on GitHub](https://github.com/IBM-Bluemix/dashdb-nodejs-helloworld){:external} -->

## Video: Introducing Db2 on Cloud
{: #intro_vid}

Watch this video to see an introduction to {{site.data.keyword.Db2_on_Cloud_short}}.

<iframe class="embed-responsive-item" id="youtubeplayer1" title="Introduction to {{site.data.keyword.Db2_on_Cloud_short}}" type="text/html" width="640" height="390" src="//www.youtube.com/embed/F_ylk44_WOg?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>

## Video: Using REST API to communicate with Db2 on Cloud
{: #vid_api}

Watch this video to see the steps required to use a RESTful API to communicate with {{site.data.keyword.Db2_on_Cloud_short}}.

<iframe class="embed-responsive-item" id="youtubeplayer2" title="Using RESTful API to communicate with {{site.data.keyword.Db2_on_Cloud_short}}" type="text/html" width="640" height="390" src="//www.youtube.com/embed/PSNBDwgf9ts?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>

## Video: Integrating Jupyter Notebooks
{: #cognos_vid}

Watch this video to see how to integrate Jupyter Notebooks with {{site.data.keyword.Db2_on_Cloud_short}}.

<iframe class="embed-responsive-item" id="youtubeplayer3" title="Integrating Jupyter notebooks" type="text/html" width="640" height="390" src="//www.youtube.com/embed/bNfH0Wzx3is?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>


