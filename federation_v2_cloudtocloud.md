--

copyright:
  years: 2020
lastupdated: "2020-06-19"

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

# Federation - SSL from cloud database to cloud database
{: #fed_v2}

Federation allows you to communicate with one or more local or remote databases.

The following steps are required to configure the federation system:

- [Federation - SSL from cloud database to cloud database](#federation---ssl-from-cloud-database-to-cloud-database)
  - [Database and host name layout](#database-and-host-name-layout)
  - [Create a wrapper](#create-a-wrapper)
  - [Create the server for a remote database](#create-the-server-for-a-remote-database)
  - [Create the user mapping](#create-the-user-mapping)
  - [Test the connection](#test-the-connection)
  - [Create a nickname](#create-a-nickname)


## Database and host name layout
{: #db_hn}

Target database where the remote table must show:

```
Hostname :               <target_host_name>
DB2 Version:             v11.5
Database Name:           BLUDB
Schema Name:             <schema_name>
```

Remote database where the table is present:

```
Hostname :              <remote_host_name>
DB2 Version:            v11.5
Service/Port Number:    <port>
User:                   <remote_user>
Password:               <remote_password>
Database Name:          BLUDB
Schema Name:            TESTDB
Table Name:             TEST1
```

The following commands have to be run from the Console of the target database instance


## Create a wrapper
{: #fed2_wrapper}

Create a wrapper by running the following command:

```
create wrapper "drdawrapper" library 'libdb2drda.so' options(DB2_FENCED 'Y')
```
{: codeblock}

```
DB20000I  The SQL command completed successfully.
```

## Create the server for a remote database
{: #fed2_serv_remote_db}

Create a server to host the remote database by running the following command:

```
create server fed_server type DB2/UDB version 11 wrapper drdawrapper authorization "<remote_user>" PASSWORD "<remote_password>" options(host '<remote_host_name>', port '<port>', dbname 'bludb', security 'SSL', password 'y')
```
{: codeblock}

```
DB20000I  The SQL command completed successfully.
```


## Create the user mapping
{: #fed2_user_map}

Create the user mapping by running the following command:

```
create user mapping for user server fed_server OPTIONS (remote_authid '<remote_user>', remote_password '<remote_password>')
```
{: codeblock}

```
DB20000I  The SQL command completed successfully.
```


## Test the connection
{: #fed2_test_conxion}

Test the connection to the new server by running the following commands:

```
db2 "set passthru fed_server"
```
{: codeblock}

```
DB20000I  The SQL command completed successfully.
```

```
db2 "select * from testdb.test1"
```
{: codeblock}

```
C1          C2
----------- -----------
         13          32

1 record(s) selected.
```

```
db2 "SET PASSTHRU RESET"
```
{: codeblock}

```
DB20000I  The SQL command completed successfully.
```


## Create a nickname
{: #fed2_nick}

Create a nickname for the remote database and test the nickname by running the following commands:
```
db2 "create nickname rmttest1 FOR fed_server.testdb.test1"
```
{: codeblock}

```
DB20000I  The SQL command completed successfully.
```

```
db2 "select * from testdb.rmttest1"
```
{: codeblock}

```
C1          C2
----------- -----------
         13          32

1 record(s) selected.
```

