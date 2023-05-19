---

copyright:
  years: 2014, 2020
lastupdated: "2023-05-05"

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

# Driver package
{: #drvr_pkg}

The {{site.data.keyword.Db2_on_Cloud_short}} driver package contains software for connecting client applications to a {{site.data.keyword.Db2_on_Cloud_short}} database. 
{: shortdesc}

## About
{: #drvr_abt}

- The driver package contains client interface tools, such as CLPPlus.
- The driver package also contains the following drivers: 
  - JDBC
  - Node.js
  - Ruby
  - ODBC
  - CLI
  - .Net
  - OLE DB
  - And more ...

## Already installed?
{: #drvr_alrdy_instld}

To verify that the driver package is already on your computer so that you can skip installing it again, or to determine the version number, you can use the [**db2level**](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.admin.cmd.doc/doc/r0009195.html){:external} command.

## Downloading
{: #drvr_dwnldng}

You can download the driver package for your operating system from the driver download center. Your web console provides a link to the site. In your web console, select **Administration > Connections**. Select the tab for your operating system.


## Installing
{: #drvr_instlng}

Install the driver package for your operating system:
- [Installing on Linux or PowerLinux](#install_drvr_pkg_linux)
- [Installing on Mac OS X](#install_drvr_pkg_mac)
- [Installing on Windows](#install_drvr_pkg_windows)

### Installing the driver package on Linux or PowerLinux
{: #drvr_install_linux}

You can install the {{site.data.keyword.Db2_on_Cloud_short}} driver package on Linux or PowerLinux by using `installDSDriver`. 
{: shortdesc}

#### Prerequisites
{: #drvr_prereq31}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

<!-- Download the Db2 driver package for your operating system from the web console and install it. -->

**On PowerLinux only**, complete the following steps to install the XL C/C++ compiler runtime package:

1. Download the XL C/C++ compiler runtime package from the FTP site. For example, to use the **wget** tool to download the runtime package for Linux little endian Ubuntu 14, issue the following command: 

   `wget ftp://public.dhe.ibm.com/software/server/POWER/Linux/rte/xlcpp/le/ubuntu/dists/trusty/main/binary-ppc64el/*`
2. Install the runtime package by issuing the following command:

   `sudo dpkg -iG *.deb` 

#### Procedure
{: #drvr_proc31}

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

#### What's next?
{: #drvr_wn}

To be able to connect your local applications or client tools to your {{site.data.keyword.Db2_on_Cloud_short}} database, [configure your local environment](#cfg_loc_env).   

### Installing the driver package on Mac OS X
{: #drvr_install_mac}

You can install the {{site.data.keyword.Db2_on_Cloud_short}} driver package on Mac OS X by using the `installDSDriver.sh` script. 
{: shortdesc}

#### Prerequisites
{: #drvr_prereq41}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

<!-- Download the Db2 driver package for your operating system from the web console and install it. -->

#### Procedure
{: #drvr_proc41}

- **For a new installation**

  1. Mount the disk image by double-clicking the `macos_dsdriver.dmg` file.
   
     A new **Finder** window opens with the contents of the disk image.

     If the **Finder** window does not open, double-click the `macos_dsdriver` icon on your desktop.
  2. In the **Finder** window, double-click the `installDSDriver.sh` file.

     The driver package is installed in the default location: `/Applications/dsdriver`.

- **For updates to your existing driver package installation**

  1. Back up current configuration files:

     a. Go the `Applications/dsdriver/cfg` folder.

     b. Copy the following files to a different folder: 
    
        `db2cli.ini`

        `db2dsdriver.cfg`
  2. Remove the currently installed driver package by right-clicking the `dsdriver` folder and selecting **Move to Trash**.
  3. Install the new driver package as described in the preceding **For a new installation** section:
     
     a. Mount the disk image by double-clicking the `macos_dsdriver.dmg` file.
     b. In the **Finder** window, double-click the `installDSDriver.sh` file.
  4. Restore the configuration files:

     Copy the `db2cli.ini` and `db2dsdriver.cfg` files that you saved from Step 1 to the `/Applications/dsdriver/cfg` folder.

#### What's next?
{: #drvr_wn41}

To be able to connect your local applications or client tools to your {{site.data.keyword.Db2_on_Cloud_short}} database, [configure your local environment](#cfg_loc_env).

### Installing the driver package on Windows
{: #drvr_install_windows}

You can install the {{site.data.keyword.Db2_on_Cloud_short}} driver package on Windows by using the installer. 
{: shortdesc}

#### Prerequisites
{: #drvr_prereq51}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

<!-- Download the driver package for your operating system from the web console and install it. -->

#### Procedure
{: #drvr_proc51}

1. Run the downloaded executable file as an administrator.

   The default installation path of the driver package is: `Program Files\IBM\IBM DATA SERVER DRIVER`
2. (*Optional*): Add the `bin` subdirectory of the driver package installation directory to your `%PATH%` environment variable (so you can run the **db2cli** command without specifying the full path to the command executable.)

#### What's next?
{: #drvr_wn51}

To be able to connect your local applications or client tools to your {{site.data.keyword.Db2_on_Cloud_short}} database, [configure your local environment](#cfg_loc_env).


<!-- ## Configuring

To connect local applications or client tools to your {{site.data.keyword.Db2_on_Cloud_short}} database, [configure your environment for your Db2 database](driver_pkg_cfg.html). -->

## Configuring your local environment
{: #drvr_cfg_loc_env}

To connect local applications and tools to your {{site.data.keyword.Db2_on_Cloud_short}} database, you need to configure your environment.  
{: shortdesc}

### Prerequisites
{: #drvr_prereq21}

Before attempting to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database, verify that you have the [prerequisites](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ov#prereqs).

<!-- 1. Install the Db2 driver package for your operating system.

   - [Installing on Windows](install_win.html)
   - [Installing on Linux or PowerLinux](install_linux.html)
   - [Installing on Mac OS X](install_mac.html)
2. Decide whether or not you will be using Secure Sockets Layer (SSL) to connect to your database.
3. Collect database details and connect credentials, including the host name of your server, and your database user ID and password. -->

### Procedure
{: #drvr_proc21}

1. Add entries to the driver configuration file, `db2dsdriver.cfg`, for your database.

   The configuration steps are different depending on whether you want to connect to your database by using SSL:

   **With SSL**

   To connect your applications and tools to your database by using SSL, enter the following commands in a command shell on Linux operating systems, at the Windows command prompt, or in a DB2 command window: 

   `db2cli writecfg add -database BLUDB -host <hostname> -port <port>`

   `db2cli writecfg add -dsn <alias> -database BLUDB -host <hostname> -port <port>`

   `db2cli writecfg add -database BLUDB -host <hostname> -port <port> -parameter "SecurityTransportMode=SSL"`

    where:

   - `<hostname>` is the host name of your server.
   - `<alias>` is an alias that you choose. The alias cannot be the same as the database name, `BLUDB`. If you want to have spaces in the alias, surround the alias with double quotation marks.
   - `<port>` is the port number assigned to your server.

   **Without SSL**

   To connect your applications and tools to your database without using SSL, enter the following commands in a command shell on Linux operating systems, at the Windows command prompt, or in a DB2 command window: 

   `db2cli writecfg add -database BLUDB -host <hostname> -port <port>`

   `db2cli writecfg add -dsn <alias> -database BLUDB -host <hostname> -port <port>`

    where:

   - `<hostname>` is the host name of your server.
   - `<alias>` is an alias that you choose. The alias cannot be the same as the database name, `BLUDB`. If you want to have spaces in the alias, surround the alias with double quotation marks.
   - `<port>` is the port number assigned to your server.


2. Test connecting by issuing the **db2cli validate** command from the command prompt:

   `db2cli validate -dsn <alias> -connect -user <userid> -passwd <password>`

   where: 
   
   - `<alias>` is an alias that you created with the **db2cli writecfg** command.
   - `<userid>` is your Db2 user ID.
   - `<password>` is your Db2 password.

3. (*Optional*): To be able to connect local ODBC applications and tools to your database, register the DSN with the ODBC driver manager:
 
   Run the following command from a command line: 

   `db2cli registerdsn -add -dsn <alias>`

   where: 

   - `<alias>` is an alias that you created with the **db2cli writecfg** command.

   By default, the DSN is created as a user DSN.



