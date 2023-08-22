---

copyright:
  years: 2021
lastupdated: "2023-08-21"

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

# Investigating latency events

For users facing latency issues when migrating from on-premise applications to on-cloud services please contact the Db2 on Cloud team and then complete the following steps to improve latency. To begin the latency improvement process, please open a support case. 

For information about opening an IBM support case, or about support levels and case severities, see: [Working with support cases](/docs/get-support?topic=get-support-open-case#open-case){:external}

The latency improvement process cannot be completed without contacting the Db2 on Cloud team at this time. 
{: important}

### Steps

1. **Set up client SSL (if not already set up)**

    For existing Db2 users, SSL would have been set up during the configuration process.

    If SSL setup is required, follow the steps outlined in Db2 documentation:  
    https://www.ibm.com/docs/en/db2/11.5?topic=ctsidc-configuring-tls-support-in-non-java-db2-clients

1. **Set up client connection**
    
   1. To enable client affinity, the Automatic Client Reroute (ACR) configuration is provided by the db2dsdriver.cfg on the db2 client machine
        
        1. Obtain the sample db2dsdriver from ```/opt/ibm/db2/V11.5/cfg/db2dsdriver.cfg.sample```

        1. Copy into ```/home/db2inst1/sqllib/cfg/```

        1. Rename to db2dsdriver.cfg

    1. The db2dsdriver.cfg is the last configuration method used to establish a connection to the db2 database. This means that db2dsdriver.cfg has the least precedence and will only be used for connecting when no other connection configurations are available. 

    1. In order for the db2dsdriver.cfg to be used for the connection, all other connection configurations need to be disabled or removed for that specific database. **Ensure that these existing configuration methods are backed up in the event that backout needs to be executed.** This includes the following:
        
        1. db2 node and database connection details (check ```db2 list node directory``` and ```db2 list database directory``` - verify connection details are not present for the database you're trying to connect to)
            - back up the connection configs before removing them
        1. db2cli.ini file (verify that this file does not exist or does not have connection details for your specific database - can be found at ```~/sqllib/cfg```)
            - Back up the db2cli.ini as db2cli.ini.bak
        1. For more details, see https://www.ibm.com/docs/en/db2/11.5?topic=file-order-precedence-obtaining-database-information

1. **Update db2dsdriver.cfg**

    1. The db2dsdriver.cfg needs to be updated with the connection parameters required for your database.
        - If there is an existing db2dsdriver.cfg, copy it to db2dsdriver.cfg.bak
    1. Refer to the db2 data server driver configuration documentation - https://www.ibm.com/docs/en/db2/11.5?topic=drivers-data-server-driver-configuration-file
    1. The preferred path would be whichever zone the client is in, regardless of where the primary is, since the primary can rotate to other zones. When the primary is in a different zone than the client, there is a 50% improvement (over no preferred path), though the fastest connection time will be achieved if the current primary is in the same zone as the client (75% improvement over no preferred path).
    1. To enable client affinity (setting a preferred path), ```<acr>...</acr>``` config is required in the db2dsdriver.cfg:
        
                <acr>
                    <parameter name="enableACR" value="true"/>
                    <!--<parameter name="enableSeamLessACR" value="true"/>-->
                    <parameter name="maxAcrRetries" value="10"/>
                    <!--maximum number of connection attempts to each server in the list of alternate servers for ACR-->
                    <parameter name="acrRetryInterval" value="5"/>
                    <!--number of seconds to wait between retries-->
                    <parameter name="affinityFailbackInterval" value="10"/>
                    <!--number of seconds to wait after the first transaction boundary to fail back to the primary server-->
                    <alternateserverlist>
                        <server name="dal10" hostname="db2-icd-preprod-us-s-759393.us-south.serviceendpoint.cloud.ibm.com" port="31014">
                        </server>
                        <server name="dal12" hostname="db2-icd-preprod-us-s-207889.us-south.serviceendpoint.cloud.ibm.com" port="31014">                        
                        </server>
                        <server name="dal13" hostname="db2-icd-preprod-us-s-747467.us-south.serviceendpoint.cloud.ibm.com" port="31014">
                        </server>
                    </alternateserverlist>
                    <affinitylist>
                        <list name="dal13_primary" serverorder="dal13,dal12,dal10">
                        </list>
                        <list name="dal12_primary" serverorder="dal12,dal13,dal10">                        
                        </list>
                        <list name="dal10_primary" serverorder="dal10,dal12,dal13">
                        </list>
                    </affinitylist>
                    <clientaffinitydefined>
                        <!--this section has specific defined affinities -->
                        <client name="client1" hostname="localhost" listname="dal10_primary">
                        </client>
                    </clientaffinitydefined>
                </acr>
            
        1. Within the ```<acr></acr>``` block, required parameters include:
            - *enableACR* - should be set to true
            - *alternateserverlist* - the list of alternate servers to try, including the primary server to connect to (note: hostname values should reference the aliases that were created during step 2 of server setup)
            - *affinitylist* - the order in which servers from alternateserverlist should be tried for connection. Affinity list ordering when primary and client are in the same zone: ```<client_zone, zone2, zone3>``` where zone2 and zone3 order does not matter. Affinitylist ordering when primary and client are in different zones: ```<client_zone, primary_zone, zone3>```
            - *clientaffinitydefined* - definition of which list from affinitylist a given client should use
    1. db2dsdriver.cfg example:

            <?xml version="1.0" encoding="UTF-8" standalone="no" ?>
            <configuration>
                <dsncollection>
                    <dsn alias="hadb" host="db2-icd-preprod-us-s-747467.us-south.serviceendpoint.cloud.ibm.com" name="BLUDB" port="31014">
                </dsncollection>
                <databases>
                    <database host="db2-icd-preprod-us-s-747467.us-south.serviceendpoint.cloud.ibm.com" name="BLUDB" port="31014">
                        <parameter name="SecurityTransportMode" value="SSL"/>
                        <parameter name="SSLServerCertificate" value="/home/db2inst1/SSL/db2_ha.crt"/>
                        <acr>
                            <parameter name="enableACR" value="true"/>
                            <!--<parameter name="enableSeamLessACR" value="true"/>-->
                            <parameter name="maxAcrRetries" value="10"/>
                            <!--maximum number of connection attempts to each server in the list of alternate servers for ACR-->
                            <parameter name="acrRetryInterval" value="5"/>
                            <!--number of seconds to wait between retries-->
                            <parameter name="affinityFailbackInterval" value="10"/>
                            <!--number of seconds to wait after the first transaction boundary to fail back to the primary server-->
                            <alternateserverlist>
                                <server name="dal10" hostname="db2-icd-preprod-us-s-759393.us-south.serviceendpoint.cloud.ibm.com" port="31014">
                                </server>
                                <server name="dal12" hostname="db2-icd-preprod-us-s-207889.us-south.serviceendpoint.cloud.ibm.com" port="31014"> <!--client is in dal12-->
                                </server>
                                <server name="dal13" hostname="db2-icd-preprod-us-s-747467.us-south.serviceendpoint.cloud.ibm.com" port="31014"> 
                                </server>
                            </alternateserverlist>
                            <affinitylist>
                                <list name="dal13_primary" serverorder="dal13,dal12,dal10">
                                </list>
                                <list name="dal12_primary" serverorder="dal12,dal13,dal10">  
                                </list>
                                <list name="dal10_primary" serverorder="dal10,dal12,dal13"> <!--primary-->
                                </list>
                 </affinitylist>
                            <clientaffinitydefined>
                                <!--this section has specific defined affinities -->
                                <client name="client1" hostname="localhost" listname="dal13_primary">
                                </client>
                            </clientaffinitydefined>
                        </acr>
                    </database>
                </databases>
            </configuration>    
            
      This configuration assumes the primary is in the dal13 zone and the client is in dal12 (therefore, a minimum of 1 network hop will still be required)
{: note}
      
    - this sample defines the db2 connection details for two different formations in preprod - a single node formation that uses the database alias ```singledb``` and an ha formation that uses the database alias ```hadb```


<!--### Optional: Test using "db2 ping", compare times
- On the client machine, as user db2inst1:

    db2 ping <db-alias> <# of pings> - ex. ```db2 ping hadb 100```-->


