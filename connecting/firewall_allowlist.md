---

copyright:
  years: 2021
lastupdated: "2023-04-21"

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

# Firewall Allowlist

If you use allowlists to control connections in your environment, you can use the following IP lists to allowlist Db2 on Cloud deployments. You should allowlist all of the subnet ranges for the _entire_ region that your deployments live in.

As new clusters in a region are created, there will be additional IP ranges that will be added. If an existing Db2oC customer adds a new instance, it may be necessary to add these new IP ranges into the firewall rules.
{:important}

### `Dallas` List
Subnet | Location
-- | --
52.116.179.72/29 | dal10
169.47.221.160/29 | dal10
169.48.136.32/29 | dal10
169.61.233.8/29 | dal10
52.117.144.16/29 | dal10
169.46.44.40/29 | dal10
169.46.55.64/29 | dal10
169.47.195.32/29 | dal10
52.116.221.96/29 | dal12
169.59.195.128/29 | dal12
169.61.143.48/29 | dal12
169.61.156.232/29 | dal12
169.47.71.16/29 | dal12
169.47.73.240/29 | dal12
169.47.74.136/29 | dal12
169.47.78.128/29 | dal12
169.61.157.120/29 | dal12
52.117.238.40/29 | dal13
52.117.249.176/29 | dal13
169.61.51.96/29 | dal13
169.62.167.128/29 | dal13
52.116.3.56/29 | dal13
169.48.70.200/29 | dal13
169.60.146.120/29 | dal13
169.60.154.184/29 | dal13
169.60.164.88/29 | dal13


### `Frankfurt` List
Subnet | Location
-- | --
159.122.98.248/29 | fra02
159.122.121.232/29 | fra02
169.50.5.8/29 | fra02
161.156.8.168/29 | fra04
161.156.91.56/29 | fra04
161.156.103.32/29 | fra04
149.81.98.128/29 | fra05
149.81.142.0/29 | fra05
149.81.181.96/29 | fra05


### `London` List
Subnet | Location
-- | --
158.175.68.168/29 | lon04
158.175.131.248/29 | lon04
141.125.88.200/29 | lon05
141.125.95.224/29 | lon05
158.176.87.208/29 | lon06
158.176.91.120/29 | lon06



### `Tokyo` List
Subnet | Location
-- | --
169.56.0.248/29 | tok02
161.202.247.16/29 | tok02
128.168.86.160/29 | tok04
128.168.86.168/29 | tok04
165.192.82.192/29 | tok05
165.192.86.232/29 | tok05

### `Washington` List
Subnet | Location
-- | --
169.55.125.224/29 | wdc04
169.55.72.120/29 | wdc04
169.60.92.72/29 | wdc06
169.60.71.40/29 | wdc06
52.117.76.136/29 | wdc07
169.62.51.8/29 | wdc07


### `Sydney` List
Subnet | Location
-- | --
168.1.11.160/29 | syd01
168.1.12.248/29 | syd01
130.198.90.72/29 | syd04
130.198.123.80/29 | syd04
135.90.89.192/29 | syd05
135.90.89.48/29 | syd05


### `Milan` List
Subnet | Location
-- | --
159.122.134.192/29 | mil01
159.122.148.216/29 | mil01

### `Montreal` List
Subnet | Location
-- | --
169.54.88.80/29 | mon01
169.54.71.136/29 | mon01


### `Sao Paulo` List
Subnet | Location
-- | --
169.57.160.160/29 | sao01
169.57.160.136/29 | sao01
169.57.199.32/29 | sao01
169.57.208.24/29 | sao01
163.107.69.232/29 | sao04
163.107.71.232/29 | sao04
163.109.72.136/29 | sao05
163.109.72.80/29 | sao05


### `Toronto` List
Subnet | Location
-- | --
169.53.186.200/29 | tor01
169.48.7.8/29/29 | tor01
169.55.169.160/29 | tor01
169.55.132.216/29 | tor01
163.74.72.240/29 | tor04
163.74.73.32/29 | tor04
163.75.74.240/29 | tor05
163.75.74.248/29 | tor05


### `Amsterdam` List
Subnet | Location
-- | --
169.51.52.168/29 | ams03
169.50.186.48/29 | ams03

