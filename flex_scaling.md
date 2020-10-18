---

copyright:
  years: 2014, 2020
lastupdated: "2020-06-22"

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

# Flexible scaling
{: #scale}

Independent scaling of storage and compute cores.  
**_Note:_** 
1. As the number of cores is increased, memory will be increased as well. 
2. Storage cannot be scaled down, once it has been increased.
{: shortdesc}


{: #flex_scale_current_plans}
## Standard Plan
The Standard plan deploys with 8GB of RAM, and 20GB of disk space.  You can then scale your plan up or down with the slider bars in the console. 

Memory can be scaled up and down in the following steps:

|Memory|
|--|
|8|
|16|
|32|
|64|

Storage can be scaled up to a maximum of 4 TB.  Once scaled up, storage cannot be scaled down.

To scale memory and storage in Console
1. Select Administration from the menu on the left
2. Select `Compute & storage` tab on the top

![Standard plan scaling](images/std_scale.png "Standard plan scaling"){: caption="Figure 1. Scaling Memory and Storage" caption-side="bottom"}


## Enterprise Plan
Your Enterprise plan initially deploys with 4 cores, 16 GB of RAM, and 20 GB of disk space. You can then scale your plan up or down with slider bars in the {{site.data.keyword.Db2_on_Cloud_short}} console by up to 56 virtual cores and 4 TB of storage. 

These dynamic adjustments typically take less than 20 minutes to complete. You can also scale CPU and RAM without any downtime by following these [guidelines](https://developer.ibm.com/answers/questions/381931/how-can-i-scale-cpu-up-and-down-without-downtime-o.html){:external}.

## Legacy Plans
{: #flex_scale_legacy_plans}

Independent scaling of RAM, storage, and compute cores. 

Your Flex plan initially deploys with 1 core, 4 GB of RAM and 2 GB of disk space. You can then scale your plan up or down with slider bars.

These dynamic adjustments typically take less than 20 minutes to complete. You can even scale CPU and RAM without any downtime by following these [guidelines](https://developer.ibm.com/answers/questions/381931/how-can-i-scale-cpu-up-and-down-without-downtime-o.html){:external}.
