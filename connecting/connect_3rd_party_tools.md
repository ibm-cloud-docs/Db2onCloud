---

copyright:
  years: 2014, 2021
lastupdated: "2021-01-05"

keywords:

subcollection: Db2onCloud

---

 
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:video: .video}

# Connecting with third-party tools
{: #connect_3rd_party}

You can connect third-party command-line interfaces, applications, and tools to your {{site.data.keyword.Db2_on_Cloud_short}} database. 
{: shortdesc}

## Data integration
{: #3rd_party_integrations}



### Segment
{: #segment}

You can integrate Segment with a {{site.data.keyword.Db2_on_Cloud_short}} database. Segment is a single platform that collects, stores, and routes your user data to hundreds of tools.
{: shortdesc}

[Segment](https://segment.com/docs/destinations/db2/){:external}



## Data visualization & BI
{: #3rd_party_vis_bi}

### Looker
{: #looker}

You can connect Looker to a {{site.data.keyword.Db2_on_Cloud_short}} database. Looker is a business intelligence app and big data analytics platform with which you can explore, analyze, and share real-time business analytics.
{: shortdesc}

[Connecting Looker](https://docs.looker.com/setup-and-management/connecting-to-db){:external}

### Tableau
{: #tableau}

These instructions explain how to connect Tableau to a {{site.data.keyword.Db2_on_Cloud_short}} database and apply to Tableau Desktop, but you can use similar steps for other Tableau tools.
{: shortdesc}

#### Prerequisites
{: #prereq_1}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

#### Procedure
{: #procedure_1}

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

These instructions explain how to connect Microsoft Excel to a {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

#### Prerequisites
{: #prereq_2}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

You must have the Db2 driver package or the IBM® Data Server Driver Package installed on your local computer. 

**Restriction**: Connections between Excel and {{site.data.keyword.Db2_on_Cloud_short}} are supported on only the Windows operating system.

#### Procedure
{: #procedure_2}

1. In the web console, go to the **Run SQL** page.    
2. Type one or more SELECT statements in the editor text box.
3. Click one of the Run options.
4. Click **Excel ODC File**.
5. Download and open the `BLUExcel.odc` file in Excel. If a security notice is displayed, click **Enable**.
6. Click **Open** to connect to the {{site.data.keyword.Db2_on_Cloud_short}} database. The **Connect To DB2 Database** dialog box opens.
7. Type the user ID and password that you use to log in to {{site.data.keyword.Db2_on_Cloud_short}}. To obtain the user ID and password, click **Connect** in the web console or **Connect > Connection Information** in the web console.
8. Ensure that the connection mode is `Share`, and then click **OK**.

#### Results
{: #results_2}

The query results are displayed in an Excel spreadsheet. These results are the same results that are displayed in the Results viewer. Now you can generate charts and reports and analyze your data by using Excel. For more information about how to generate charts and reports and how to run SQL queries on your data from the web console, see: 
- [Tutorial: Generating charts and reports by using Excel](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.analytics.doc/doc/explore_excel_reports.html){: external}
- [Analyzing with Excel](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.analytics.doc/doc/exploreexcel.html){: external}



## Data science
{: #3rd_party_sci}

### SAS
{: #sas}

These instructions explain how to create a connection from SAS to a {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

#### Prerequisites
{: #prereq_3}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

#### Procedure
{: #procedure_3}

For steps on how to connect from SAS to a {{site.data.keyword.Db2_on_Cloud_short}} database, see the SAS documentation:
- [SAS/ACCESS Interface to DB2 under UNIX and PC Hosts](https://documentation.sas.com/?docsetId=acreldb&docsetTarget=p1dzq4zjg1iycgn16l4xj9nnvibt.htm&docsetVersion=9.4&locale=en){: external}




