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
52.116.179.72/29 | Dal 10
169.47.221.160/29 | Dal 10
169.48.136.32/29 | Dal 10
169.61.233.8/29 | Dal 10
52.117.144.16/29 | Dal 10
169.46.44.40/29 | Dal 10
169.46.55.64/29 | Dal 10
169.47.195.32/29 | Dal 10
52.116.221.96/29 | Dal 12
169.59.195.128/29 | Dal 12
169.61.143.48/29 | Dal 12
169.61.156.232/29 | Dal 12
52.117.238.40/29 | Dal 13
52.117.249.176/29 | Dal 13
169.61.51.96/29 | Dal 13
169.62.167.128/29 | Dal 13
52.116.3.56/29 | Dal 13
169.48.70.200/29 | Dal 13
169.60.146.120/29 | Dal 13
169.60.154.184/29 | Dal 13
169.60.164.88/29 | Dal 13


### `Frankfurt` List
Subnet | Location
-- | --
159.122.98.248/29 | Fra 02
159.122.121.232/29 | Fra 02
169.50.5.8/29 | Fra 02
161.156.8.168/29 | Fra 04
161.156.91.56/29 | Fra 04
161.156.103.32/29 | Fra 04
149.81.98.128/29 | Fra 05
149.81.142.0/29 | Fra 05
149.81.181.96/29 | Fra 05


### `London` List
Subnet | Location
-- | --
158.175.68.168/29 | Lon 04
158.175.131.248/29 | Lon 04
141.125.88.200/29 | Lon 05
141.125.95.224/29 | Lon 05
158.176.87.208/29 | Lon 06
158.176.91.120/29 | Lon 06



### `Tokyo` List
Subnet | Location
-- | --
169.56.0.248/29 | Tok 02
161.202.247.16/29 | Tok 02
128.168.86.160/29 | Tok 04
128.168.86.168/29 | Tok 04
165.192.82.192/29 | Tok 05
165.192.86.232/29 | Tok 05

### `Washington` List
Subnet | Location
-- | --
169.55.125.224/29 | Wdc 04
169.55.72.120/29 | Wdc 04
169.60.92.72/29 | Wdc 06
169.60.71.40/29 | Wdc 06
52.117.76.136/29 | Wdc 07
169.62.51.8/29 | Wdc 07


### `Sydney` List
Subnet | Location
-- | --
168.1.11.160/29 | Syd 01
168.1.12.248/29 | Syd 01
130.198.90.72/29 | Syd 04
130.198.123.80/29 | Syd 04
135.90.89.192/29 | Syd 05
135.90.89.48/29 | Syd 05


### `Milan` List
Subnet | Location
-- | --
159.122.134.192/29 | Mil 01
159.122.148.216/29 | Mil 01

### `Montreal` List
Subnet | Location
-- | --
169.54.88.80/29 | Mon 01
169.54.71.136/29 | Mon 01


### `Sao Paulo` List
Subnet | Location
-- | --
169.57.160.160/29 | Sao 01
169.57.160.136/29 | Sao 01
169.57.199.32/29 | Sao 01
169.57.208.24/29 | Sao 01
163.107.69.232/29 | Sao 04
163.107.71.232/29 | Sao 04
163.109.72.136/29 | Sao 05
163.109.72.80/29 | Sao 05


### `Toronto` List
Subnet | Location
-- | --
169.53.186.200/29 | Tor 01
169.48.7.8/29/29 | Tor 01 
169.55.169.160/29 | Tor 01
169.55.132.216/29 | Tor 01
163.74.72.240/29 | Tor 04
163.74.73.32/29 | Tor 04
163.75.74.240/29 | Tor 05
163.75.74.248/29 | Tor 05


### `Amsterdam` List
Subnet | Location
-- | --
169.51.52.168/29 | Ams 03
169.50.186.48/29 | Ams 03

