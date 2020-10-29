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

# Connecting programmatically by using the driver package
{: #con_program}

The {{site.data.keyword.Db2_on_Cloud_short}} driver package contains software for connecting client applications to a {{site.data.keyword.Db2_on_Cloud_short}} database. 
{: shortdesc}

## JDBC
{: #con_prog_jdbc}

Define a connection between a Java™ application and the {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

### Prerequisites
{: #prereq61}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

<!-- Before you can connect to your database, you must perform the following steps:

- [Verify prerequisites](prereqs.html), including installing driver packages, configuring your local environment, and downloading SSL certificates (if needed)
- Collect [connection information](credentials.html), including database details such as host name and port numbers, and connection credentials such as user ID and password -->

### Procedure
{: #proc61}

#### Enterprise/Standard Plans
In each Java application, specify the user ID and password by including the **DriverManager.getConnection** method, and then include one of the following JDBC URL strings:

- For a connection with SSL:

  `jdbc:db2://<host_name>:<port>/bludb:user=<userid>;password=<your_password>;sslConnection=true;`


#### Legacy Plans

In each Java application, specify the user ID and password by including the **DriverManager.getConnection** method, and then include one of the following JDBC URL strings:

- For a connection with SSL:

  `jdbc:db2://<host_name>:50001/BLUDB:sslConnection=true;`

- For a connection without SSL:

  `jdbc:db2://<host_name>:50000/BLUDB`

## .NET
{: #con_prog_net}

Define a connection between a .NET application and your {{site.data.keyword.Db2_on_Cloud_short}} database. 
{: shortdesc}

### Prerequisites
{: #prereq71}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

<!-- Before you can connect to your database, you must perform the following steps:

- [Verify prerequisites](prereqs.html), including installing driver packages, configuring your local environment, and downloading SSL certificates (if needed)
- Collect [connection information](credentials.html), including database details such as host name and port numbers, and connection credentials such as user ID and password -->

### Procedure
{: #proc71}

The following steps show you how to connect your application to the database with .NET.

1. From a command prompt, enter the following commands. These commands create new entries in the driver configuration file (`db2dsdriver.cfg`) on your computer and set the connection attributes. You need to do this step only one time.
    #### Enterprise/Standard Plans
    - For a connection with SSL:

      `db2cli writecfg add -database BLUDB -host <hostname> -port <port>`

      `db2cli writecfg add -dsn <alias> -database BLUDB -host <hostname> -port <port>`

      `db2cli writecfg add -database BLUDB -host <hostname> -port <port> -parameter "SecurityTransportMode=SSL"`

      where:

      `<hostname>`: The host name of the server.

      `<port>`: The port number of the server
    
      `<alias>`: The name for a DSN alias that you want to use to establish the .NET connection. Choose a name that is meaningful to you; for example, `analytics`.


   #### Legacy Plans     
   - For a connection with SSL:

     `db2cli writecfg add -database BLUDB -host <hostname> -port 50001`

     `db2cli writecfg add -dsn <alias> -database BLUDB -host <hostname> -port 50001`

     `db2cli writecfg add -database BLUDB -host <hostname> -port 50001 -parameter "SecurityTransportMode=SSL"`

     where:

     `<hostname>`: The host name of the server.
    
     `<alias>`: The name for a DSN alias that you want to use to establish the .NET connection. Choose a name that is meaningful to you; for example, `analytics`. 

   - For a connection without SSL:

     `db2cli writecfg add -database BLUDB -host <hostname> -port 50000`

     `db2cli writecfg add -dsn <alias> -database BLUDB -host <hostname> -port 50000`

2. (*Optional*): To verify the .NET connection to the database, enter the following command at a command prompt:

   `testconn40 "DATABASE=<alias>;UID=<user_id>;PWD=<password>;"`

   where:

   `<alias>`: The name of the DSN alias that you created with the **db2cli writecfg** command in step 1.
    
   `<user_id>`: Your {{site.data.keyword.Db2_on_Cloud_short}} user ID. 
    
   `<password>`: The password that you use to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database. 

### Example
{: #ex71}

The following syntax shows sample C# code that uses the .NET driver to make a connection to the database.

```
using System;
using IBM.Data.DB2;

namespace dotNetSSLTest
{
    class Program
    {
        static void Main(string[] args)
        {
            DB2Command MyDB2Command = null;
            // Use the dsn alias that you defined in db2dsdriver.cfg with the db2cli writecfg command in step 1.
            String MyDb2ConnectionString = "database=alias;uid=userid;pwd=password;"; 
            DB2Connection MyDb2Connection = new DB2Connection(MyDb2ConnectionString);
            MyDb2Connection.Open();
            MyDB2Command = MyDb2Connection.CreateCommand();
            MyDB2Command.CommandText = "SELECT branch_code, city from GOSALES.BRANCH";
            Console.WriteLine(MyDB2Command.CommandText);

            DB2DataReader MyDb2DataReader = null;
            MyDb2DataReader = MyDB2Command.ExecuteReader();
            Console.WriteLine("BRANCH\tCITY");
            Console.WriteLine("============================");
            while (MyDb2DataReader.Read())
            {
                for (int i = 0; i <= 1; i++)
                {
                    try
                    {
                        if (MyDb2DataReader.IsDBNull(i))
                        {
                            Console.Write("NULL");
                        }
                        else
                        {
                            Console.Write(MyDb2DataReader.GetString(i));
                        }
                    }
                    catch (Exception e)
                    {
                        Console.Write(e.ToString());
                    }
                    Console.Write("\t"); 

                }
                Console.WriteLine("");
            }
            MyDb2DataReader.Close();
            MyDB2Command.Dispose();
            MyDb2Connection.Close();
        }
    }
}
```
{: codeblock}

## ODBC or CLI
{: #con_prog_odbc_cli}

Define a connection between a Microsoft Windows ODBC or CLI application and a {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

### Prerequisites
{: #prereq81}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

<!-- Before you can connect to your database, you must perform the following steps:

- [Verify prerequisites](prereqs.html), including installing driver packages, configuring your local environment, and downloading SSL certificates (if needed)
- Collect [connection information](credentials.html), including database details such as host name and port numbers, and connection credentials such as user ID and password -->

### Procedure
{: #proc81}

1. In a command shell on Linux operating systems, at the Windows command prompt, or in the Db2 command window on Windows operating systems, enter the following commands:

   **Note**: These commands create new entries in the driver configuration file (`db2dsdriver.cfg`) on your computer and set the connection attributes. You need to do this step only one time.
   
   #### Enterprise/Standard Plans
    - For a connection with SSL:

      `db2cli writecfg add -database BLUDB -host <hostname> -port <port> -parameter "SecurityTransportMode=SSL"`

      `db2cli writecfg add -dsn <alias> -database BLUDB -host <hostname> -port <port>`



   #### Legacy Plans
   - For a connection with SSL:

     `db2cli writecfg add -database BLUDB -host <hostname> -port 50001 -parameter "SecurityTransportMode=SSL"`

     `db2cli writecfg add -dsn <alias> -database BLUDB -host <hostname> -port 50001`

   - For a connection without SSL:

     `db2cli writecfg add -database BLUDB -host <hostname> -port 50000`

     `db2cli writecfg add -dsn <alias> -database BLUDB -host <hostname> -port 50000`

   where:

   `<hostname>` is the host name of the server

   `<port>` is the port number of the server

   `<alias>` is a DSN alias that you choose
    
2. (*Optional*): To test the connection to the database, run this command from the command prompt:

   `db2cli validate -dsn <alias> -connect -user <user_id> -passwd <password>`

   where:

   `<alias>` is the DSN alias that you created with the **db2cli writecfg** command

   `<user_id>` is from the connect credentials that you collected beforehand

   `<password>` is from the connect credentials that you collected beforehand

3. (*Optional*): To register the data source name (DSN) with Microsoft ODBC Driver Manager and to work with Microsoft ODBC applications, run the following command. By default, the DSN is created as user DSN.

   `db2cli registerdsn -add -dsn <alias>`

   where:
        
   `<alias>` is the DSN alias that you created with the **db2cli writecfg** command

## ODBC Data Source Administrator
{: #con_prog_odbc_dsa}

Use the Microsoft ODBC Data Source Administrator tool to define a connection between an ODBC or CLI application and a {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

### Prerequisites
{: #prereq91}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

<!-- Before you can connect to your database, you must perform the following steps:

- [Verify prerequisites](prereqs.html), including installing driver packages, configuring your local environment, and downloading SSL certificates (if needed)
- Collect [connection information](credentials.html), including database details such as host name and port numbers, and connection credentials such as user ID and password -->

### Procedure
{: #proc91}

1. Install the [Db2 driver package](/docs/Db2onCloud?topic=Db2onCloud-drvr_pkg).

2. Open ODBC Data Source Administrator and create either a User DSN or System DSN for the Db2 driver package.
    
3. Click **Advanced** Settings. Enter following CLI parameters with their values for the {{site.data.keyword.Db2_on_Cloud_short}} server: **Hostname**, **Port**, and **Database**.
    
4. For an SSL connection, enter CLI parameter **Security** with value `SSL`.
    
5. Click **Apply**.
    
6. To test the connection, return to main page of ODBC Data Source Administrator. Click **Configure** for the DSN that you created. Enter the user ID and password for the server and click **Connect**.

## PHP
{: #con_prog_php}

Define a connection between a PHP application and a {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

### Prerequisites
{: #prereq101}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

<!-- Before you can connect to your database, you must perform the following steps:

- [Verify prerequisites](prereqs.html), including installing driver packages, configuring your local environment, and downloading SSL certificates (if needed)
- Collect [connection information](credentials.html), including database details such as host name and port numbers, and connection credentials such as user ID and password -->

### Procedure
{: #proc101}

#### Scenario 1: Connecting from outside {{site.data.keyword.Bluemix_notm}}:
{: #scen1}

1. Download the [Db2 driver package](/docs/Db2onCloud?topic=Db2onCloud-drvr_pkg) from the web console, and then install the driver package on the machine where your PHP application will run.
                
2. Use the [`odbc_connect` function](http://php.net/manual/en/function.odbc-connect.php){:external} to connect to the BLUDB database.
    
   PHP code example:

   ```
   <?php
   $database = "BLUDB";          # Get these database details from
   $hostname = "<Host-name>";    # the web console
   $user     = "<User-ID >";     #
   $password = "<Password>";     #
   $port     = "<non-ssl_port>"; #
   $ssl_port = "<port>";         #
   # Build the connection string
   #
   $driver  = "DRIVER={IBM DB2 ODBC DRIVER};";
   $dsn     = "DATABASE=$database; " .
              "HOSTNAME=$hostname;" .
              "PORT=$port; " .
              "PROTOCOL=TCPIP; " .
              "UID=$user;" .
              "PWD=$password;";
   $ssl_dsn = "DATABASE=$database; " .
              "HOSTNAME=$hostname;" .
              "PORT=$ssl_port; " .
              "PROTOCOL=TCPIP; " .
              "UID=$user;" .
              "PWD=$password;" .
              "SECURITY=SSL;";
   $conn_string = $driver . $dsn;     # Non-SSL
   $conn_string = $driver . $ssl_dsn; # SSL
   # Connect
   #
   $conn = odbc_connect( $conn_string, "", "" );
   if( $conn )
   {
       echo "Connection succeeded.";
       # Disconnect
       #
       odbc_close( $conn );
   }
   else
   {
       echo "Connection failed.";
   }
   ?>
   ```
   {: codeblock}

   Saving this PHP code example to a script file called `C:\sample.php` and then running the script from a command line produces the following output:

   ```
   C:\> php –f sample.php

   Connection succeeded.
   ```

#### Scenario 2: Connecting from a PHP web app in {{site.data.keyword.Bluemix_notm}}
{: #scen2}

1. From the {{site.data.keyword.Bluemix_notm}} catalog, create a new PHP App.
        
2. From the "Getting Started" section of the new PHP App in your {{site.data.keyword.Bluemix_notm}} dashboard, download the App starter code to your local work directory.
        
3. In your {{site.data.keyword.Bluemix_notm}} dashboard, create a new connection from your Db2 service to your new PHP App. (Creating this Connection in {{site.data.keyword.Bluemix_notm}} makes the `VCAP_SERVICES` environment variable available to your PHP App. The `VCAP_SERVICES` environment variable contains database details for your Db2 service. Using `VCAP_SERVICES` is more convenient than hardcoding the database details in your PHP App.)
        
4. In your local working directory, update the `index.php` file to connect to the BLUDB database by using the [`db2_connect` function](http://php.net/manual/en/function.db2-connect.php){:external}.
        
   Example:

   ```
   <!DOCTYPE html>
   <html>
   <head>
       <title>PHP Starter Application</title>
       <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
       <link rel="stylesheet" href="style.css" />
   </head>
   <body>
   <?php
   if( getenv( "VCAP_SERVICES" ) )
   {
       # Get database details from the VCAP_SERVICES environment variable
       #
       # *This can only work if you have used the Bluemix dashboard to 
       # create a connection from your dashDB service to your PHP App.
       #
       $details  = json_decode( getenv( "VCAP_SERVICES" ), true );
       $dsn      = $details [ "dashDB" ][0][ "credentials" ][ "dsn" ];
       $ssl_dsn  = $details [ "dashDB" ][0][ "credentials" ][ "ssldsn" ];
       # Build the connection string
       #
       $driver = "DRIVER={IBM DB2 ODBC DRIVER};";
       $conn_string = $driver . $dsn;     # Non-SSL
       $conn_string = $driver . $ssl_dsn; # SSL
       $conn = db2_connect( $conn_string, "", "" );
       if( $conn )
       {
           echo "<p>Connection succeeded.</p>";
           db2_close( $conn );
       }
       else
       {
           echo "<p>Connection failed.</p>";
       }
   }
   else
   {
       echo "<p>No credentials.</p>";
   }
   ?>
   </body>
   </html>
   ```
   {: codeblock}

5. From your local working directory, push the updates to {{site.data.keyword.Bluemix_notm}} by following the instructions in the "Getting Started" section of the PHP App in your {{site.data.keyword.Bluemix_notm}} dashboard. Then, restart the App in {{site.data.keyword.Bluemix_notm}} and view the App in a browser.



