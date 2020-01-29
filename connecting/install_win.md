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

# Installing the driver package on Windows
{: #install_dr_pkg_windows}

You can install the {{site.data.keyword.Db2_on_Cloud_short}} driver package on Windows by using the installer. 
{: shortdesc}

## Prerequisites
{: #prereq51}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

<!-- Download the driver package for your operating system from the web console and install it. -->

## Procedure
{: #proc51}

1. Run the downloaded executable file as an administrator.

   The default installation path of the driver package is: `Program Files\IBM\IBM DATA SERVER DRIVER`
2. (*Optional*): Add the `bin` subdirectory of the driver package installation directory to your `%PATH%` environment variable (so you can run the **db2cli** command without specifying the full path to the command executable.)

## What's next?
{: #wn51}

To be able to connect your local applications or client tools to your {{site.data.keyword.Db2_on_Cloud_short}} database, [configure your local environment](/docs/Db2onCloud?topic=Db2onCloud-cfg_loc_env#cfg_loc_env).