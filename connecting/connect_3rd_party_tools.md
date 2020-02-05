---

copyright:
  years: 2014, 2020
lastupdated: "2020-02-04"

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

# Connecting to third-party tools
{: #connect_3rd_party}

You can connect third-party command-line interfaces, applications, and tools to your {{site.data.keyword.Db2_on_Cloud_short}} database. 
{: shortdesc}

## Data integration
{: #3rd_party_integrations}

<!--
### Informatica
{: #informatica}

You can connect Informatica to {{site.data.keyword.Db2_on_Cloud_short}} to help you manage your data.
{: shortdesc}

Watch this video to see how to integrate {{site.data.keyword.Db2_on_Cloud_short}} with Informatica Cloud.

<iframe class="embed-responsive-item" id="youtubeplayer1" title="DB2 Connections - Lightening Fast How-To with Informatica Cloud" type="text/html" width="640" height="390" src="//www.youtube.com/embed/TUiS_HstLnU?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>
-->

### Segment
{: #segment}

You can integrate Segment with a {{site.data.keyword.Db2_on_Cloud_short}} database. Segment is a single platform that collects, stores, and routes your user data to hundreds of tools.
{: shortdesc}

[Segment](https://segment.com/docs/destinations/db2/){:external}

<!--
### Aginity Workbench
{: #aginity_wb}

These instructions explain how to connect Aginity Workbench to a {{site.data.keyword.Db2_on_Cloud_short}} database. You can use Aginity Workbench to migrate IBM PureData for Analytics (Netezza) data models and data to {{site.data.keyword.Db2_on_Cloud_short}}.
{: shortdesc}

#### Prerequisites
{: #prereq6}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

#### Procedure
{: #proc6}

1. Download and install Aginity Workbench.
2. Determine your ODBC DSN from the connection information that you noted earlier.
3. Launch Aginity Workbench. If the database connection dialog box does not open automatically, open it by clicking **Connect** on the toolbar.
4. [Establish a database connection](https://www.aginity.com/documentation/WB/dashDB/Default.htm#Aginity_Topics/Aginity_Workbench/Database_Connection_Dialog_Box.htm){:external}. Use the host name, user ID, and password from the connection information that you noted earlier.
-->

## Data visualization & BI
{: #3rd_party_vis_bi}

### Looker
{: #looker}

You can connect Looker to a {{site.data.keyword.Db2_on_Cloud_short}} database. Looker is a business intelligence app and big data analytics platform with which you can explore, analyze, and share real-time business analytics.
{: shortdesc}

[Connecting Looker](https://docs.looker.com/setup-and-management/connecting-to-db){:external}

### Tableau
{: #tableau}

These instructions explain how to connect Tableau to a {{site.data.keyword.Db2_on_Cloud_short}} database and apply to Tableau Desktop<!--version 8.x-->, but you can use similar steps for other Tableau tools.
{: shortdesc}

#### Prerequisites
{: #prereq8}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

#### Procedure
{: #proc8}

1. In Tableau Desktop, open the window or page in your tool that is used to define a database connection.
2. From the start page, click **Connect to data**.
3. From the **Data Sources** list, select the data source or driver to use for your database connection. In the **On a server** section of the list, select **IBM Db2**.
4. From the **IBM DB2 Connection** window, enter the connection information by using the definitions in Table 1.
5. Click **Connect** to establish the connection. Tableau offers several options for connecting to your data. To make full use of your {{site.data.keyword.Db2_on_Cloud_short}} database, choose the **Connect Live** option.

| Tableau field | Db2 connections information field |
|---------------|-----------------------------------|
| Step 1: Enter a server name | Host name |
| Step 2: Port | Port number |
| Step 3: Enter a database on the server | Database name |
| Username | User ID |
| Password | Password |
{: caption="Table 1. Fields in Tableau for connection information" caption-side="top"}

### Microsoft Excel
{: #excel}

These instructions explain how to connect Microsoft Excel <!--2010-->to a {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

#### Prerequisites
{: #prereq9}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

You must have the Db2 driver package or the IBM® Data Server Driver Package installed on your local computer. 

**Restriction**: Connections between Excel and {{site.data.keyword.Db2_on_Cloud_short}} are supported on only the Windows operating system.

#### Procedure
{: #proc9}

1. In the web console, go to the **Run SQL** page.    
2. Type one or more SELECT statements in the editor text box.
3. Click one of the Run options.
4. Click **Excel ODC File**.
5. Download and open the `BLUExcel.odc` file in Excel. If a security notice is displayed, click **Enable**.
6. Click **Open** to connect to the {{site.data.keyword.Db2_on_Cloud_short}} database. The **Connect To DB2 Database** dialog box opens.
7. Type the user ID and password that you use to log in to {{site.data.keyword.Db2_on_Cloud_short}}. To obtain the user ID and password, click **Connect** in the web console or **Connect > Connection Information** in the web console.
8. Ensure that the connection mode is `Share`, and then click **OK**.

#### Results
{: #results2}

The query results are displayed in an Excel spreadsheet. These are the same results that are displayed in the Results viewer. Now you can generate charts and reports and analyze your data by using Excel. For more information about how to do this and how to run SQL queries on your data from the web console, see: 
- [Tutorial: Generating charts and reports by using Excel](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.analytics.doc/doc/explore_excel_reports.html){:external}
- [Analyzing with Excel](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.analytics.doc/doc/exploreexcel.html){:external}

<!--
### Esri ArcGIS for Desktop
{: #esri_arcgis}

You can connect Esri ArcGIS for Desktop to a {{site.data.keyword.Db2_on_Cloud_short}} database and then use it to analyze and visualize geospatial data.
{: shortdesc}

#### Prerequisites
{: #prereq10}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

You must have the Db2 driver package or the IBM® Data Server Driver Package installed on your computer.

#### Procedure
{: #proc10}

1. Determine your ODBC DSN data from the [connection information](/docs/Db2onCloud/connecting?topic=Db2onCloud-db_details_cxn_creds#db_details_cxn_creds) that you collected beforehand.

2. Create a new connection:
      
   a. In the ArcCatalog Catalog tree, open the Database Connections node and click **Add Database Connection**.
        
   b. In the Database Connections wizard:
   - Select **DB2** from the Database Platform drop-down list.
   - Enter the following string in the **Data source** field:
     ```
     HostName=<hostname>;Port=<port>;Database=<database>;
     CLIENTBUFFERSUNBOUNDLOBS=1;LOBCACHESIZE=50000000;
     FET_BUF_SIZE=256K  
     ```

     where `<hostname>`, `<port>`, and `<database>` are placeholders that represent the host name, port number, and database name that you noted earlier.
            
   - Select **Database authentication** as the authentication type.
            
   - Specify your user name and password (the user ID and password that you noted earlier) in the corresponding fields.
            
   - Press **OK**.
        
     ![Database Connections wizard](images/2_gs_conn.jpg "Database Connections wizard"){: caption="Figure 1. Database Connections wizard" caption-side="bottom"}

#### Results
{: #results3}

The ArcCatalog component of Esri ArcGIS for Desktop is now connected to your {{site.data.keyword.Db2_on_Cloud_short}} database. 
-->

## Data science
{: #3rd_party_sci}

### SAS
{: #sas}

These instructions explain how to create a connection from SAS to a {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

#### Prerequisites
{: #prereq12}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

#### Procedure
{: #proc12}

For steps on how to connect from SAS to a {{site.data.keyword.Db2_on_Cloud_short}} database, see the SAS documentation:
- [SAS/ACCESS Interface to DB2 under UNIX and PC Hosts](https://documentation.sas.com/?docsetId=acreldb&docsetTarget=p1dzq4zjg1iycgn16l4xj9nnvibt.htm&docsetVersion=9.4&locale=en){:external}

<!--
### R development environment
{: #r_dev_env}

Instead of using the RStudio® environment that is integrated within IBM Watson Studio, you might prefer to use your own, locally installed R development environment. For example, you might have your own RStudio installation, or you might prefer to use some other development tool such as Rcmdr or Rattle. These instructions explain how to connect an R development environment to a {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

#### Prerequisites
{: #prereq13}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

#### Procedure
{: #proc13}

1. In your local R environment, install the `ibmdbR` package by entering the following command:

   `install.packages("ibmdbR")`

   Your local R environment accesses the Comprehensive R Archive Network (CRAN) and automatically downloads and installs the `ibmdbR` package and any prerequisite packages that are not already installed.
    
2. Create an ODBC driver connection between your R development environment and your {{site.data.keyword.Db2_on_Cloud_short}} database:
        
   a. [Set up your database as an ODBC data source](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cli_and_odbc_applications.html){:external}.
        
   b. Open your locally installed R development environment.
        
   c. At the R prompt, enter the following statements to create the connection. Replace the placeholders with the [connection information](/docs/Db2onCloud/connecting?topic=Db2onCloud-db_details_cxn_creds#db_details_cxn_creds) that you collected beforehand.

   - If your locally installed R development environment runs in the {{site.data.keyword.Db2_on_Cloud_short}} database:

     ```
     library(ibmdbR)
     host.name <- "placeholderForYourHostName"
     port <-"placeholderForPortNumber" # 50000 if not using SSL or 50001 if using SSL
     user.name <-"placeholderForYourUserName"
     pwd <- "placeholderForYourPassword"
     con.text <- paste("placeholderForYourDSNName;DRIVER=BLUDB",
                       ";Database=BLUDB",
                       ";Hostname=",host.name,
                       ";Port=",port,
                       ";PROTOCOL=TCPIP",
                       ";UID=", user.name,
                       ";PWD=",pwd,sep="")
     # Connect to using a odbc Driver Connection string to a remote database
     con <- idaConnect(con.text)
     ```

   - If your locally installed R development environment does not run in the {{site.data.keyword.Db2_on_Cloud_short}} database:

     ```
     library(ibmdbR)
     driver.name <- "{placeholderForYourDriverName}"
     db.name <- "placeholderForYourDatabaseName"
     host.name <- "placeholderForYourHostName"
     port <-"placeholderForYourPort"
     user.name <-"placeholderForYourUserName"
     pwd <- "placeholderForYourPassword"
     con.text <- paste("placeholderForYourDSNName;DRIVER=",driver.name,
                       ";Database=",db.name,
                       ";Hostname=",host.name,
                       ";Port=",port,
                       ";PROTOCOL=TCPIP",
                       ";UID=", user.name,
                       ";PWD=",pwd,sep="")
     # Connect to using a odbc Driver Connection string to a remote database
     con <- idaConnect(con.text)
     ```

     The statement that is used to create the connection object uses the `idaConnect()` method, not the `odbcConnect()` or `odbcDriverConnect()` methods.
     {: note}
        
   d. Initialize the analytics package by issuing the following R command:

   `idaInit(con)`

   e. To test whether the connection is working, issue the following R command:

   `idaShowTables()`

   The console displays a list of all of the tables and views in the current schema.
-->


