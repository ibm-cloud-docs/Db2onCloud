---

copyright:
  years: 2014, 2019
lastupdated: "2018-10-15"

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

# Data science
{: #ds}

You can also connect external applications and tools to {{site.data.keyword.Db2_on_Cloud_short}} and use them to further manage or analyze your data. 
{: shortdesc}

## Watson Studio
{: #watson_studio}

After you create a project in IBM Watson Studio (formerly Data Science Experience), you add data assets to it so that you can work with data. All the collaborators in the project are automatically authorized to access the data in the project.
{: shortdesc}

How you add data and from where you can add data differs between legacy and IBM Watson projects. IBM Watson projects use {{site.data.keyword.Bluemix_notm}} Object Storage. The project is a legacy project if it uses Object Storage OpenStack Swift. 

### To create a new connection in an IBM Watson project:

1. Click **Add to project > Connection**.
    
2. Choose a data source.
    
3. Enter the connection information required for your data source. Typically, you need to provide information like the host, port number, user name, and password.
    
4. You can discover assets from connections to {{site.data.keyword.Db2_on_Cloud_short}}, which gives you the ability to add all tables from the connection as data assets to a project. Select **Discover data assets** and choose a project.
    
5. Click **Create**. The connection appears on the **Assets** page.

Watch this video to see how to create a connection and add connected data to a project.

<iframe class="embed-responsive-item" id="youtubeplayer" title="Create a connection and add connected data to a project" type="text/html" width="640" height="390" src="//www.youtube.com/embed/U7-gCbo4QtM?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>

### To create a new connection in a legacy project:

1. From your project's **Assets** page, click the **Find and add data** icon.
    
2. On the **Connections** pane, click **Create Connection**.

3. Enter a name and description and choose a Service Category:

   **Data Service** = {{site.data.keyword.Bluemix_notm}} data service

   When you choose **Data Service**, your existing {{site.data.keyword.Bluemix_notm}} data services appear in the **Service Instance** list.

4. Choose the service or database server from the list.

5. Enter the connection information:

   When you choose **Data Service**, your existing {{site.data.keyword.Bluemix_notm}} data services appear in the **Service Instance** list.
    
6. Click **Create**. The connection is available to all legacy projects.
    
7. On the **Connections** pane, select the connection and click **Apply**.

To add an existing connection to a legacy project:

1. From your project's **Assets** page, click the **Find and add data** icon.
    
2. On the **Connections** pane, select the connection and click **Apply**.

## SPSS Statistics
{: #spss_stats}

These instructions explain how to create a connection from IBM® SPSS® Statistics to a {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

### Prerequisites
{: #prereq11}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

### Procedure
{: #proc11}

1. In SPSS Statistics, click **File > Open Database > New Query**.
    
2. In the Database Wizard, click **Add ODBC data source**.
    
3. Use the ODBC Data Source Administrator window to add an ODBC data source name (DSN) for the {{site.data.keyword.Db2_on_Cloud_short}} database:
        
   a. On the **User DSN** tab, click **Add**.

   b. On the Create New Data Source window, select the driver that is named **IBM DB2 ODBC DRIVER** and click **Finish**.

   Be sure that the driver that you select is not a driver with a similar name such as `IBM DB2® ODBC DRIVER - DB2COPY`. If the driver does not appear in the list, exit SPSS Statistics, then download and install the driver. See [Driver package](/docs/Db2onCloud/connecting?topic=Db2onCloud-dr_pkg#dr_pkg).
        
   c. In the ODBC IBM Driver - Add window, enter a data source name (usually the name of the database you are connecting to), and click **Add**.
        
   d. From the CLI/ODBC Settings window, on the **Data Source** tab, enter the user ID and password from the [connection information](/docs/Db2onCloud/connecting?topic=Db2onCloud-db_details_cxn_creds#db_details_cxn_creds) that you collected beforehand.
        
   e. On the Advanced Settings page, for each of the following parameters, click **Add** to open the Add CLI Parameter window to begin the step, and click **OK** to return to the Advanced Settings page:
            
   - Select the `Database` parameter, then click **OK** to open the CLI/ODBC Settings window. In the **Pending Value** field, enter the database name from the connection information that you collected beforehand.

   - Select the `Hostname` parameter, then click **OK** to open the CLI/ODBC Settings window. In the **Pending Value** field, enter the host name from the connection information that you collected beforehand.

   - Select the `Port` parameter, then click **OK** to open the CLI/ODBC Settings window. In the **Pending Value** field, enter the port number from the connection information that you collected beforehand.
            
   - Select the `Protocol` parameter, then click **OK** to open the CLI/ODBC Settings window. Select **TCP/IP**.
        
   f. Click **OK** to return to the ODBC Data Source Administrator window.
        
   g. On the **User DSN** tab, select the data source name, then click **Configure**.
        
   h. On the CLI/ODBC Settings window, click **Connect** to test the connection.
            
   - If the connection is successful, click **OK** to return to the ODBC Data Source Administrator window, and then click **OK** to exit the window.
            
   - If the connection is not successful, note and correct any errors before you test the connection again.

## SAS
{: #sas}

These instructions explain how to create a connection from SAS to a {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

### Prerequisites
{: #prereq12}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

### Procedure
{: #proc12}

For steps on how to connect from SAS to a {{site.data.keyword.Db2_on_Cloud_short}} database, see the SAS documentation:
- [SAS/ACCESS Interface to DB2 under UNIX and PC Hosts](https://documentation.sas.com/?docsetId=acreldb&docsetTarget=p1dzq4zjg1iycgn16l4xj9nnvibt.htm&docsetVersion=9.4&locale=en){:external}

## R development environment
{: #r_dev_env}

Instead of using the RStudio® environment that is integrated within IBM Watson Studio, you might prefer to use your own, locally-installed R development environment. For example, you might have your own RStudio installation, or you might prefer to use some other development tool such as Rcmdr or Rattle. These instructions explain how to connect an R development environment to a {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

### Prerequisites
{: #prereq13}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

### Procedure
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

