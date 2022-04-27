---

copyright:
  years: 2021
lastupdated: "2021-08-23"

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
169.46.44.40/29 | Dal 10
169.47.221.160/29| Dal 10
169.46.55.64/29 | Dal 10
169.61.233.8/29 | Dal 10
169.61.157.120/29 | Dal 12
169.61.143.48/29 | Dal 12
169.47.74.136/29 | Dal 12
169.61.156.232/29 | Dal 12
169.60.146.120/29 | Dal 13
52.117.238.40/29 | Dal 13
169.60.154.184/29 | Dal 13
169.61.51.96/29 | Dal 13



### `Frankfurt` List
Subnet | Location
-- | --
169.50.5.8/29 | Fra 02
159.122.98.248/29 | Fra 02
161.156.8.168/29 | Fra 04
161.156.103.32/29 | Fra 04
149.81.181.96/29 | Fra 05
149.81.142.0/29 | Fra 05


### `London` List
Subnet | Location
-- | --
158.175.131.248/29 | Lon 04
141.125.88.200/29 | Lon 05
158.176.91.120/29 | Lon 06



### `Tokyo` List
Subnet | Location
-- | --
169.56.0.248/29 | Tok 02
128.168.86.168/29 | Tok 04
165.192.82.192/29 | Tok 05

### `Washington` List
Subnet | Location
-- | --
169.55.125.224/29 | Wdc 04
169.60.71.40/29 | Wdc 06
52.117.76.136/29 | Wdc 07


### `Sydney` List
Subnet | Location
-- | --
168.1.11.160/29 | Syd 01
130.198.123.80/29 | Syd 04
135.90.89.192/29 | Syd 05

### `Milan` List
Subnet | Location
-- | --
159.122.134.192/29 | Mil 01

### `Montreal` List
Subnet | Location
-- | --
169.54.88.80/29 | Mon 01


### `Sao Paulo` List
Subnet | Location
-- | --
169.57.160.160/29 | Sao 01
163.107.69.232/29 | Sao 04
163.109.72.136/29 | Sao 05



### `Toronto` List
Subnet | Location
-- | --
169.53.186.200/29 | Tor 01
163.74.72.240/29 | Tor 04
163.75.74.240/29 | Tor 05


### `Amsterdam` List
Subnet | Location
-- | --
169.51.52.168/29 | Ams 03
