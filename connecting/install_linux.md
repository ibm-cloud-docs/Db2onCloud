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

# Installing the driver package on Linux or PowerLinux
{: #install_dr_pkg_linux}

You can install the {{site.data.keyword.Db2_on_Cloud_short}} driver package on Linux or PowerLinux by using `installDSDriver`. 
{: shortdesc}

## Prerequisites
{: #prereq31}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

<!-- Download the Db2 driver package for your operating system from the web console and install it. -->

**On PowerLinux only**, complete the following steps to install the XL C/C++ compiler runtime package:

1. Download the XL C/C++ compiler runtime package from the FTP site. For example, to use the **wget** tool to download the runtime package for Linux little endian Ubuntu 14, issue the following command: 

   `wget ftp://public.dhe.ibm.com/software/server/POWER/Linux/rte/xlcpp/le/ubuntu/dists/trusty/main/binary-ppc64el/*`
2. Install the runtime package by issuing the following command:

   `sudo dpkg -iG *.deb` 

## Procedure
{: #proc31}

1. Decompress the compressed driver package file that you downloaded earlier.

   Example: 

   `gunzip file_name.tar.gz`

   `tar -xvf file_name.tar`

    A `dsdriver` subdirectory is created in the directory where you ran the decompression commands.
2. Extract the Java and ODBC/CLI drivers.

   a. In the `dsdriver` subdirectory, run the **installDSDriver** command.
   
   The **installDSDriver** command creates the `db2profile` and `db2cshrc` script files in the `dsdriver` directory.

   b. Run one of the following script files based on your shell environment:

   - **Bash or Korn shell**: `source db2profile`
   - **C shell**: `source db2cshrc`

## What's next?
{: #wn}

To be able to connect your local applications or client tools to your {{site.data.keyword.Db2_on_Cloud_short}} database, [configure your local environment](/docs/Db2onCloud?topic=Db2onCloud-cfg_loc_env#cfg_loc_env).   




