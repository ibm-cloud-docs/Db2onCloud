---

copyright:
  years: 2014, 2019
lastupdated: "2018-09-25"

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

# Connecting programmatically with .NET
{: #con_prog_net}

Define a connection between a .NET application and your {{site.data.keyword.Db2_on_Cloud_short}} database. 
{: shortdesc}

## Prerequisites
{: #prereq71}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

<!-- Before you can connect to your database, you must perform the following steps:

- [Verify prerequisites](prereqs.html), including installing driver packages, configuring your local environment, and downloading SSL certificates (if needed)
- Collect [connection information](credentials.html), including database details such as host name and port numbers, and connection credentials such as user ID and password -->

## Procedure
{: #proc71}

The following steps show you how to connect your application to the database with .NET.

1. From a command prompt, enter the following commands. These commands create new entries in the driver configuration file (`db2dsdriver.cfg`) on your computer and set the connection attributes. You need to do this step only one time.
        
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

## Example
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

