---

copyright:
  years: 2014, 2025
lastupdated: "2025-04-20"

keywords: HADR, Automatic Client Reroute Setup, ACR, high availability disaster recovery

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

# Automatic Client Reroute Setup (ACR)

This ACR workaround is intended for use on Db2 On Cloud High Availibility (HA) instances with private CSE enabled. It should not be used for any HA instances that are connecting to Db2 over public endpoints.

### Client-side Setup

1. **Settings required for client connections with ACR enabled**

   The client side requires the following ACR related settings in order to successfully reconnect to the db2 database after a failover or connection interruption.

```
    enableClientAffinitiesList=1
    clientRerouteAlternateServerName=hostname,hostname (hostname is the same as the primary host)
    clientRerouteAlternatePortNumber=port,port (port is the same SSL port)
    enableSeamlessFailover=1
    loginTimeout=30 (can vary based on application)
    blockingReadConnectionTimeout=30 (can vary based on application)
    maxRetriesForClientReroute=100 (can vary based on application)
    retryIntervalForClientReroute=5 (can vary based on application)
```

**Note:**
1. retryIntervalForClientReroute*maxRetriesForClientReroute needs to be greater than blockingReadConnectionTimeout.
2. blockingReadConnectionTimeout will impact normal workload as well. Make sure the value is enough to handle the daily workload, but also not too long to trigger the failover.


### Test Connection using JDBC connection string

The following connection string can be used to test connection and ACR during a failover scenario.

    jdbc:db2://$HOSTNAME:$PORT/BLUDB:sslConnection=true;sslCertLocation=$CERT_LOCATION;enableClientAffinitiesList=1;maxRetriesForClientReroute=10;retryIntervalForClientReroute=5;clientRerouteAlternatePortNumber=$PORT,$PORT;clientRerouteAlternateServerName=$HOSTNAME,$HOSTNAME;enableSeamlessFailover=1;loginTimeout=30;blockingReadConnectionTimeout=30;user=$USER;password=$PASSWORD;
