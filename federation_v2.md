---

copyright:
  years: 2014, 2025
lastupdated: "2025-03-20"

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

# Federation - SSL from local to cloud database
{: #fed_v2}

Federation allows you to communicate with one or more local or remote databases.

The following steps are required to configure the federation system:

1. [Database and host name layout](#db_hn)
2. [Test for federation](#fed2_test)
3. [Create and connect to local database](#fed2_create_connect_local_db)
4. [Create the wrapper](#fed2_wrapper)
5. [Create the server for a remote database](#fed2_serv_remote_db)
6. [Create the user mapping](#fed2_user_map)
7. [Test the connection](#fedv2_test_conxion)
8. [Create a nickname](#fed2_nick)


## Database and host name layout
{: #db_hn}

Local database target where the remote table must show:

```
Hostname :               <local_host_name>
DB2 Version:             v11.5
Instance Name:           db2inst1
Password:                <local_password>
Database Name:           LOCALDB
Schema Name:             DB2INST1
```

Remote database where the table is present:

```
Hostname :              <remote_host_name>
DB2 Version:            v11.5
Instance Name:          db2inst1
Service/Port Number:    30850
User:                   <remote_user>
Password:               <remote_password>
Database Name:          BLUDB
Schema Name:            DB2INST1
Table Name:             TEST1
```


## Test for federation
{: #fed2_test}

Test to see if federation is enabled on your local machine, run the following command:

```
db2 get dbm cfg | grep -i federated
```
{: codeblock}

```
Federated Database System Support           (FEDERATED) = NO
```

If federation is not enabled, then enable it by using the following commands:

```
db2 update dbm cfg using federated yes
```
{: codeblock}

```
db2stop
```
{: codeblock}

```
db2start
```
{: codeblock}

## Create and connect to local database
{: #fed2_create_connect_local_db}

Create a local database and connect to it by running the following commands:

```
db2 create db localdb
```
{: codeblock}

```
DB20000I  The CREATE DATABASE command completed successfully.
```

```
db2 connect to localdb
```
{: codeblock}

```
Database Connection Information

Database server        = DB2/LINUXX8664 11.5.1.0
SQL authorization ID   = DB2INST1
Local database alias   = LOCALDB
```


## Create a wrapper
{: #fed2_wrapper}

Create a wrapper by running the following command:

```
db2 "create wrapper drdawrapper library 'libdb2drda.so' options(DB2_FENCED 'Y')"
```
{: codeblock}

```
DB20000I  The SQL command completed successfully.
```

## Create the server for a remote database
{: #fed2_serv_remote_db}

Create a server to host the remote database by running the following command:

```
db2 "create server fed_server type DB2/UDB version 11 wrapper drdawrapper authorization \"<remote_user>\" PASSWORD \"<remote_password>\" options(host '<remote_host_name>', port '30850', dbname 'bludb', security 'SSL', password 'y')"
```
{: codeblock}

```
DB20000I  The SQL command completed successfully.
```


## Create the user mapping
{: #fed2_user_map}

Create the user mapping by running the following command:

```
db2 "create user mapping for db2inst1 server fed_server OPTIONS (remote_authid '<remote_user>', remote_password '<remote_password>')"
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

DB20000I  The SQL command completed successfully.
```
{: codeblock}

```
db2 "select * from db2inst1.test1"


C1          C2
----------- -----------
         13          32
1 record(s) selected.
```
{: codeblock}


```
db2 "SET PASSTHRU RESET"

DB20000I  The SQL command completed successfully.
```
{: codeblock}


## Create a nickname
{: #fed2_nick}

Create a nickname for the remote database and test the nickname by running the following commands:
```
db2 "create nickname db2inst1.rmttest1 FOR fed_server.db2inst1.test1"

DB20000I  The SQL command completed successfully.
```
{: codeblock}

```
db2 "select * from db2inst1.rmttest1"

C1          C2
----------- -----------
         13          32

1 record(s) selected.
```
{: codeblock}