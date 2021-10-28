---

copyright:
  years: 2014, 2021
lastupdated: "2021-10-28"

keywords: recovery, database

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

# Recovering a deleted database instance

When a service instance is deleted, it is put in a suspend state for 7 days after which its removed.  The deleted instance can be recovered within 7 days of deletion by following these steps.

The user must be logged into their IBMCloud account to be able to recover an instance.

## Listing instances available for recovery
The following command list the deleted instances that are available for reclamation:
```
ibmcloud resource reclamations
```

Example:
```
>$ ibmcloud resource reclamations
List all resource reclamations
OK
ID                                     Resource Instance ID                   Entity CRN                                                                                                                         State            Target Time
835bdb40-b33b-43b4-a1f6-e234433334   d670d057-34c2-4430-8071-bafb0dfddse108   crn:v1:bluemix:public:dashdb-for-transactions:us-south:a/a8a1951114b2d2esddf59d2d01:d670d057-34c2-4430-8071-ba23443108::   SCHEDULED        2021-10-27T14:08:22Z
```


## Recovering the deleted the instance
The following command will recover the deleted service instance:
```
ibmcloud resource reclamation-restore <ID>
```

Example:
```
>$ ibmcloud resource reclamation-restore "835bdb40-b33b-43b4-a1f6-e234433334"
Submitting request to restore resource reclamation 835bdb40-b33b-43b4-a1f6-e234433334 under account 
OK
Request to restore reclamation 835bdb40-b33b-43b4-a1f6-e234433334 was submitted
```

Issuing a `ibmcloud resource reclamations` will now show the service instnace in a **RESTORING** state

Example:
```
>$ ibmcloud resource reclamations
List all resource reclamations
OK
ID                                     Resource Instance ID                   Entity CRN                                                                                                                         State            Target Time
835bdb40-b33b-43b4-a1f6-e234433334   d670d057-34c2-4430-8071-bafb0dfddse108   crn:v1:bluemix:public:dashdb-for-transactions:us-south:a/a8a1951114b2d2esddf59d2d01:d670d057-34c2-4430-8071-ba23443108::   RESTORING        2021-10-27T14:08:22Z
```

Once the service instance has been restore it will appear in `Resources` under `Services and software` on the IBMCloud dashboard.