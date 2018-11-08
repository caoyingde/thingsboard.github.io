---
layout: docwithnav
assignees:
  - ashvayka
title: Upgrade instructions
description: ThingsBoard IoT platform upgrade instructions
---

# upgrade-instructions

*  [Upgrading to 1.0.3](upgrade-instructions.md#upgrading-to-103)
*  [Upgrading to 1.1.0](upgrade-instructions.md#upgrading-to-110)
*  [Upgrading to 1.2.0](upgrade-instructions.md#upgrading-to-120)
  *  [Ubuntu/CentOS](upgrade-instructions.md#ubuntucentos)
  *  [Windows](upgrade-instructions.md#windows)
*  [Upgrading to 1.2.1](upgrade-instructions.md#upgrading-to-121)
  *  [Ubuntu/CentOS](upgrade-instructions.md#ubuntucentos-1)
  *  [Windows](upgrade-instructions.md#windows-1)
*  [Upgrading to 1.2.2](upgrade-instructions.md#upgrading-to-122)
  *  [Ubuntu/CentOS](upgrade-instructions.md#ubuntucentos-2)
  *  [Windows](upgrade-instructions.md#windows-2)
*  [Upgrading to 1.2.3](upgrade-instructions.md#upgrading-to-123)
  *  [Ubuntu/CentOS](upgrade-instructions.md#ubuntucentos-3)
  *  [Windows](upgrade-instructions.md#windows-3)
*  [Upgrading to 1.3.0](upgrade-instructions.md#upgrading-to-130)
  *  [Ubuntu/CentOS](upgrade-instructions.md#ubuntucentos-4)
  *  [Windows](upgrade-instructions.md#windows-4)
*  [Upgrading to 1.3.1](upgrade-instructions.md#upgrading-to-131)
  *  [Ubuntu/CentOS](upgrade-instructions.md#ubuntucentos-5)
  *  [Windows](upgrade-instructions.md#windows-5)
*  [Upgrading to 1.4.0](upgrade-instructions.md#upgrading-to-140)
  *  [Ubuntu/CentOS](upgrade-instructions.md#ubuntucentos-6)
  *  [Windows](upgrade-instructions.md#windows-6)
*  [Upgrading to 2.0.0](upgrade-instructions.md#upgrading-to-200)
  *  [Ubuntu/CentOS](upgrade-instructions.md#ubuntucentos-7)
  *  [Windows](upgrade-instructions.md#windows-7)
*  [Upgrading to 2.0.1](upgrade-instructions.md#upgrading-to-201)
  *  [Ubuntu/CentOS](upgrade-instructions.md#ubuntucentos-8)
  *  [Windows](upgrade-instructions.md#windows-8)
*  [Upgrading to 2.0.2](upgrade-instructions.md#upgrading-to-202)
  *  [Ubuntu/CentOS](upgrade-instructions.md#ubuntucentos-9)
  *  [Windows](upgrade-instructions.md#windows-9)
*  [Upgrading to 2.0.3](upgrade-instructions.md#upgrading-to-203)
  *  [Ubuntu/CentOS](upgrade-instructions.md#ubuntucentos-10)
  *  [Windows](upgrade-instructions.md#windows-10)
*  [Upgrading to 2.1.0](upgrade-instructions.md#upgrading-to-210)
  *  [Ubuntu/CentOS](upgrade-instructions.md#ubuntucentos-11)
  *  [Windows](upgrade-instructions.md#windows-11)

## Upgrading to 1.0.3

These steps are applicable for 1.0, 1.0.1 and 1.0.2 ThingsBoard versions.

#### ThingsBoard package download

#### ThingsBoard service upgrade

#### Database upgrade

This step is required only if you are upgrading from 1.0 or 1.0.1 versions. Please use following instruction to update your single node instance:

```bash
# Download upgrade scripts
$ wget https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.0.3/upgrade_1.0_1.0.2.sh
$ wget https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.0.3/system_widgets_1.0_1.0.2.cql

# Launch main script
$ chmod +x upgrade_1.0_1.0.2.sh
$ ./upgrade_1.0_1.0.2.sh
```

#### Start the service

```bash
$ sudo service thingsboard start
```

## Upgrading to 1.1.0

These steps are applicable for 1.0.3 ThingsBoard version.

#### ThingsBoard package download

#### ThingsBoard service upgrade

#### Database upgrade

Please use the following instruction to update your single node instance:

```bash
# Download upgrade scripts
$ wget https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.1.0/upgrade_1.0.3_1.1.0.sh
$ wget https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.1.0/system_widgets_1.0.3_1.1.0.cql

# Launch main script
$ chmod +x upgrade_1.0.3_1.1.0.sh
$ ./upgrade_1.0.3_1.1.0.sh
```

#### Start the service

```bash
$ sudo service thingsboard start
```

## Upgrading to 1.2.0

These steps are applicable for 1.1.0 ThingsBoard version.

### Ubuntu/CentOS

#### ThingsBoard package download

#### ThingsBoard service upgrade

#### Database upgrade

```bash
# Download upgrade scripts
$ wget https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.0/upgrade_1.1.0_1.2.0.sh
$ wget https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.0/system_widgets.cql

# Launch main script
$ chmod +x upgrade_1.1.0_1.2.0.sh
$ ./upgrade_1.1.0_1.2.0.sh
```

#### Start the service

```bash
$ sudo service thingsboard start
```

### Windows

#### ThingsBoard package download

Download ThingsBoard installation archive for Windows: [thingsboard-windows-1.2.zip](https://github.com/thingsboard/thingsboard/releases/download/v1.2/thingsboard-windows-1.2.zip).

#### ThingsBoard service upgrade

* Make a backup of previous ThingsBoard configuration located in \\conf \(for ex. C:\thingsboard\conf\).
* Uninstall the previous version of ThingsBoard service by running **uninstall.bat** located in ThingsBoard install dir.

**NOTE** Scripts listed above should be executed using Administrator Role.

```text
C:\thingsboard>uninstall.bat
```

* Remove ThingsBoard install dir.
* Unzip installation archive to ThingsBoard install dir.
* Compare your old ThingsBoard configuration files \(from the backup you made in the first step\) with new ones.
* Run **install.bat** script to install the new version of ThingsBoard as a Windows service.

```text
C:\thingsboard>install.bat
```

#### Database upgrade

* Download upgrade scripts to some folder:
  * [upgrade\_1.1.0\_1.2.0.bat](https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.0/upgrade_1.1.0_1.2.0.bat)
  * [system\_widgets.cql](https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.0/system_widgets.cql)
* Execute **upgrade\_1.1.0\_1.2.0.bat** \(**NOTE** This script should be executed using Administrative Role\)

```text
upgrade_1.1.0_1.2.0.bat
```

#### Start the service

```text
net start thingsboard
```

## Upgrading to 1.2.1

These steps are applicable for 1.2.0 ThingsBoard version.

### Ubuntu/CentOS

#### ThingsBoard package download

#### ThingsBoard service upgrade

#### Database upgrade

```bash
# Download upgrade scripts
$ wget https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.1/upgrade_1.2.0_1.2.1.sh
$ wget https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.1/schema_update.cql
$ wget https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.1/system_widgets.cql

# Launch main script
$ chmod +x upgrade_1.2.0_1.2.1.sh
$ ./upgrade_1.2.0_1.2.1.sh
```

#### Start the service

```bash
$ sudo service thingsboard start
```

### Windows

#### ThingsBoard package download

Download ThingsBoard installation archive for Windows: [thingsboard-windows-1.2.1.zip](https://github.com/thingsboard/thingsboard/releases/download/v1.2.1/thingsboard-windows-1.2.1.zip).

#### ThingsBoard service upgrade

* Make a backup of previous ThingsBoard configuration located in \\conf \(for ex. C:\thingsboard\conf\).
* Uninstall the previous version of ThingsBoard service by running **uninstall.bat** located in ThingsBoard install dir.

**NOTE** Scripts listed above should be executed using Administrator Role.

```text
C:\thingsboard>uninstall.bat
```

* Remove ThingsBoard install dir.
* Unzip installation archive to ThingsBoard install dir.
* Compare your old ThingsBoard configuration files \(from the backup you made in the first step\) with new ones.
* Run **install.bat** script to install the new version of ThingsBoard as a Windows service.

```text
C:\thingsboard>install.bat
```

#### Database upgrade

* Download upgrade scripts to some folder:
  * [upgrade\_1.2.0\_1.2.1.bat](https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.1/upgrade_1.2.0_1.2.1.bat)
  * [schema\_update.cql](https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.1/schema_update.cql)
  * [system\_widgets.cql](https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.1/system_widgets.cql)
* Execute **upgrade\_1.2.0\_1.2.1.bat** \(**NOTE** This script should be executed using Administrative Role\)

```text
upgrade_1.2.0_1.2.1.bat
```

#### Start the service

```text
net start thingsboard
```

## Upgrading to 1.2.2

These steps are applicable for 1.2.1 ThingsBoard version.

### Ubuntu/CentOS

#### ThingsBoard package download

#### ThingsBoard service upgrade

#### Database upgrade

```bash
# Download upgrade scripts
$ wget https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.2/upgrade_1.2.1_1.2.2.sh
$ wget https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.2/system_widgets.cql

# Launch main script
$ chmod +x upgrade_1.2.1_1.2.2.sh
$ ./upgrade_1.2.1_1.2.2.sh
```

#### Start the service

```bash
$ sudo service thingsboard start
```

### Windows

#### ThingsBoard package download

Download ThingsBoard installation archive for Windows: [thingsboard-windows-1.2.2.zip](https://github.com/thingsboard/thingsboard/releases/download/v1.2.2/thingsboard-windows-1.2.2.zip).

#### ThingsBoard service upgrade

* Make a backup of previous ThingsBoard configuration located in \\conf \(for ex. C:\thingsboard\conf\).
* Uninstall the previous version of ThingsBoard service by running **uninstall.bat** located in ThingsBoard install dir.

**NOTE** Scripts listed above should be executed using Administrator Role.

```text
C:\thingsboard>uninstall.bat
```

* Remove ThingsBoard install dir.
* Unzip installation archive to ThingsBoard install dir.
* Compare your old ThingsBoard configuration files \(from the backup you made in the first step\) with new ones.
* Run **install.bat** script to install the new version of ThingsBoard as a Windows service.

```text
C:\thingsboard>install.bat
```

#### Database upgrade

* Download upgrade scripts to some folder:
  * [upgrade\_1.2.1\_1.2.2.bat](https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.2/upgrade_1.2.1_1.2.2.bat)
  * [system\_widgets.cql](https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.2/system_widgets.cql)
* Execute **upgrade\_1.2.1\_1.2.2.bat** \(**NOTE** This script should be executed using Administrative Role\)

```text
upgrade_1.2.1_1.2.2.bat
```

#### Start the service

```text
net start thingsboard
```

## Upgrading to 1.2.3

These steps are applicable for 1.2.2 ThingsBoard version.

### Ubuntu/CentOS

#### ThingsBoard package download

#### ThingsBoard service upgrade

#### Database upgrade

```bash
# Download upgrade scripts
$ wget https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.3/upgrade_1.2.2_1.2.3.sh
$ wget https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.3/schema_update.cql
$ wget https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.3/system_widgets.cql

# Launch main script
$ chmod +x upgrade_1.2.2_1.2.3.sh
$ ./upgrade_1.2.2_1.2.3.sh
```

#### Start the service

```bash
$ sudo service thingsboard start
```

### Windows

#### ThingsBoard package download

Download ThingsBoard installation archive for Windows: [thingsboard-windows-1.2.3.zip](https://github.com/thingsboard/thingsboard/releases/download/v1.2.3/thingsboard-windows-1.2.3.zip).

#### ThingsBoard service upgrade

* Make a backup of previous ThingsBoard configuration located in \\conf \(for ex. C:\thingsboard\conf\).
* Uninstall the previous version of ThingsBoard service by running **uninstall.bat** located in ThingsBoard install dir.

**NOTE** Scripts listed above should be executed using Administrator Role.

```text
C:\thingsboard>uninstall.bat
```

* Remove ThingsBoard install dir.
* Unzip installation archive to ThingsBoard install dir.
* Compare your old ThingsBoard configuration files \(from the backup you made in the first step\) with new ones.
* Run **install.bat** script to install the new version of ThingsBoard as a Windows service.

```text
C:\thingsboard>install.bat
```

#### Database upgrade

* Download upgrade scripts to some folder:
  * [upgrade\_1.2.2\_1.2.3.bat](https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.3/upgrade_1.2.2_1.2.3.bat)
  * [schema\_update.cql](https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.3/schema_update.cql)
  * [system\_widgets.cql](https://raw.githubusercontent.com/thingsboard/thingsboard.github.io/master/docs/user-guide/install/resources/1.2.3/system_widgets.cql)
* Execute **upgrade\_1.2.2\_1.2.3.bat** \(**NOTE** This script should be executed using Administrative Role\)

```text
upgrade_1.2.2_1.2.3.bat
```

#### Start the service

```text
net start thingsboard
```

## Upgrading to 1.3.0

These steps are applicable for 1.2.3 ThingsBoard version.

### Ubuntu/CentOS

#### ThingsBoard package download

#### ThingsBoard service upgrade

**NOTE:** Package installer will ask you to merge your thingsboard configuration. It is preferred to use **merge option** to make sure that all your previous parameters will not be overwritten.  
Please make sure that you set database.type parameter value \(in the file **/etc/thingsboard/conf/thingsboard.yml**\) to "cassandra" instead of "sql" in order to upgrade your cassandra database:

```text
database:
    type: "${DATABASE_TYPE:cassandra}" # cassandra OR sql
```

```bash
# Execute upgrade script
$ sudo /usr/share/thingsboard/bin/install/upgrade.sh --fromVersion=1.2.3
```

#### Start the service

```bash
$ sudo service thingsboard start
```

### Windows

#### ThingsBoard package download

Download ThingsBoard installation archive for Windows: [thingsboard-windows-1.3.zip](https://github.com/thingsboard/thingsboard/releases/download/v1.3/thingsboard-windows-1.3.zip).

#### ThingsBoard service upgrade

* Stop ThingsBoard service if it is running.

```text
net stop thingsboard
```

* Make a backup of previous ThingsBoard configuration located in \\conf \(for ex. C:\thingsboard\conf\).
* Remove ThingsBoard install dir.
* Unzip installation archive to ThingsBoard install dir.
* Compare your old ThingsBoard configuration files \(from the backup you made in the first step\) with new ones.
* Please make sure that you set database.type parameter value \(in the file **\\conf\thingsboard.yml**\) to "cassandra" instead of "sql" in order to upgrade your cassandra database:

  ```text
  database:
      type: "${DATABASE_TYPE:cassandra}" # cassandra OR sql
  ```

* Run **upgrade.bat** script to upgrade ThingsBoard to the new version.

**NOTE** Scripts listed above should be executed using Administrator Role.

```text
C:\thingsboard>upgrade.bat --fromVersion=1.2.3
```

#### Start the service

```text
net start thingsboard
```

## Upgrading to 1.3.1

These steps are applicable for 1.3.0 ThingsBoard version.

### Ubuntu/CentOS

#### ThingsBoard package download

#### ThingsBoard service upgrade

**NOTE:** Package installer may ask you to merge your thingsboard configuration. It is preferred to use **merge option** to make sure that all your previous parameters will not be overwritten.  
Please make sure that you set database.type parameter value \(in the file **/etc/thingsboard/conf/thingsboard.yml**\) to "cassandra" instead of "sql" in order to upgrade your cassandra database:

```text
database:
    type: "${DATABASE_TYPE:cassandra}" # cassandra OR sql
```

```bash
# Execute upgrade script
$ sudo /usr/share/thingsboard/bin/install/upgrade.sh --fromVersion=1.3.0
```

#### Start the service

```bash
$ sudo service thingsboard start
```

### Windows

#### ThingsBoard package download

Download ThingsBoard installation archive for Windows: [thingsboard-windows-1.3.1.zip](https://github.com/thingsboard/thingsboard/releases/download/v1.3.1/thingsboard-windows-1.3.1.zip).

#### ThingsBoard service upgrade

* Stop ThingsBoard service if it is running.

```text
net stop thingsboard
```

* Make a backup of previous ThingsBoard configuration located in \\conf \(for ex. C:\thingsboard\conf\).
* Remove ThingsBoard install dir.
* Unzip installation archive to ThingsBoard install dir.
* Compare your old ThingsBoard configuration files \(from the backup you made in the first step\) with new ones.
* Please make sure that you set database.type parameter value \(in the file **\\conf\thingsboard.yml**\) to "cassandra" instead of "sql" in order to upgrade your cassandra database:

  ```text
  database:
      type: "${DATABASE_TYPE:cassandra}" # cassandra OR sql
  ```

* Run **upgrade.bat** script to upgrade ThingsBoard to the new version.

**NOTE** Scripts listed above should be executed using Administrator Role.

```text
C:\thingsboard>upgrade.bat --fromVersion=1.3.0
```

#### Start the service

```text
net start thingsboard
```

## Upgrading to 1.4.0

These steps are applicable for 1.3.1 ThingsBoard version.

### Ubuntu/CentOS

#### ThingsBoard package download

#### ThingsBoard service upgrade

**NOTE:** Package installer will ask you to merge your thingsboard configuration. It is preferred to use **merge option** to make sure that all your previous parameters will not be overwritten.  
Please make sure that you set database.type parameter value \(in the file **/etc/thingsboard/conf/thingsboard.yml**\) to "cassandra" instead of "sql" in order to upgrade your cassandra database:

```text
database:
    type: "${DATABASE_TYPE:cassandra}" # cassandra OR sql
```

```bash
# Execute upgrade script
$ sudo /usr/share/thingsboard/bin/install/upgrade.sh --fromVersion=1.3.1
```

#### Start the service

```bash
$ sudo service thingsboard start
```

### Windows

#### ThingsBoard package download

Download ThingsBoard installation archive for Windows: [thingsboard-windows-1.4.zip](https://github.com/thingsboard/thingsboard/releases/download/v1.4/thingsboard-windows-1.4.zip).

#### ThingsBoard service upgrade

* Stop ThingsBoard service if it is running.

```text
net stop thingsboard
```

* Make a backup of previous ThingsBoard configuration located in \\conf \(for ex. C:\thingsboard\conf\).
* Remove ThingsBoard install dir.
* Unzip installation archive to ThingsBoard install dir.
* Compare your old ThingsBoard configuration files \(from the backup you made in the first step\) with new ones.
* Please make sure that you set database.type parameter value \(in the file **\\conf\thingsboard.yml**\) to "cassandra" instead of "sql" in order to upgrade your cassandra database:

  ```text
  database:
      type: "${DATABASE_TYPE:cassandra}" # cassandra OR sql
  ```

* Run **upgrade.bat** script to upgrade ThingsBoard to the new version.

**NOTE** Scripts listed above should be executed using Administrator Role.

```text
C:\thingsboard>upgrade.bat --fromVersion=1.3.1
```

#### Start the service

```text
net start thingsboard
```

## Upgrading to 2.0.0

These steps are applicable for 1.4.0 ThingsBoard version.

### Ubuntu/CentOS

#### ThingsBoard package download

#### ThingsBoard service upgrade

**NOTE:** Package installer will ask you to merge your thingsboard configuration. It is preferred to use **merge option** to make sure that all your previous parameters will not be overwritten.  
Please make sure that you set database.type parameter value \(in the file **/etc/thingsboard/conf/thingsboard.yml**\) to "cassandra" instead of "sql" in order to upgrade your cassandra database:

```text
database:
    type: "${DATABASE_TYPE:cassandra}" # cassandra OR sql
```

```bash
# Execute upgrade script
$ sudo /usr/share/thingsboard/bin/install/upgrade.sh --fromVersion=1.4.0
```

#### Start the service

```bash
$ sudo service thingsboard start
```

### Windows

#### ThingsBoard package download

Download ThingsBoard installation archive for Windows: [thingsboard-windows-2.0.zip](https://github.com/thingsboard/thingsboard/releases/download/v2.0/thingsboard-windows-2.0.zip).

#### ThingsBoard service upgrade

* Stop ThingsBoard service if it is running.

```text
net stop thingsboard
```

* Make a backup of previous ThingsBoard configuration located in \\conf \(for ex. C:\thingsboard\conf\).
* Remove ThingsBoard install dir.
* Unzip installation archive to ThingsBoard install dir.
* Compare your old ThingsBoard configuration files \(from the backup you made in the first step\) with new ones.
* Please make sure that you set database.type parameter value \(in the file **\\conf\thingsboard.yml**\) to "cassandra" instead of "sql" in order to upgrade your cassandra database:

  ```text
  database:
      type: "${DATABASE_TYPE:cassandra}" # cassandra OR sql
  ```

* Run **upgrade.bat** script to upgrade ThingsBoard to the new version.

**NOTE** Scripts listed above should be executed using Administrator Role.

```text
C:\thingsboard>upgrade.bat --fromVersion=1.4.0
```

#### Start the service

```text
net start thingsboard
```

## Upgrading to 2.0.1

These steps are applicable for 2.0.0 ThingsBoard version.

### Ubuntu/CentOS

#### ThingsBoard package download

#### ThingsBoard service upgrade

**NOTE:** Package installer will ask you to merge your thingsboard configuration. It is preferred to use **merge option** to make sure that all your previous parameters will not be overwritten.  
Please make sure that you set database.type parameter value \(in the file **/etc/thingsboard/conf/thingsboard.yml**\) to "cassandra" instead of "sql" in order to upgrade your cassandra database:

```text
database:
    type: "${DATABASE_TYPE:cassandra}" # cassandra OR sql
```

#### Start the service

```bash
$ sudo service thingsboard start
```

### Windows

#### ThingsBoard package download

Download ThingsBoard installation archive for Windows: [thingsboard-windows-2.0.1.zip](https://github.com/thingsboard/thingsboard/releases/download/v2.0.1/thingsboard-windows-2.0.1.zip).

#### ThingsBoard service upgrade

* Stop ThingsBoard service if it is running.

```text
net stop thingsboard
```

* Make a backup of previous ThingsBoard configuration located in \\conf \(for ex. C:\thingsboard\conf\).
* Remove ThingsBoard install dir.
* Unzip installation archive to ThingsBoard install dir.
* Compare your old ThingsBoard configuration files \(from the backup you made in the first step\) with new ones.
* Please make sure that you set database.type parameter value \(in the file **\\conf\thingsboard.yml**\) to "cassandra" instead of "sql" in order to upgrade your cassandra database:

  ```text
  database:
      type: "${DATABASE_TYPE:cassandra}" # cassandra OR sql
  ```

#### Start the service

```text
net start thingsboard
```

## Upgrading to 2.0.2

These steps are applicable for 2.0.1 ThingsBoard version.

### Ubuntu/CentOS

#### ThingsBoard package download

#### ThingsBoard service upgrade

**NOTE:** Package installer will ask you to merge your thingsboard configuration. It is preferred to use **merge option** to make sure that all your previous parameters will not be overwritten.  
Please make sure that you set database.type parameter value \(in the file **/etc/thingsboard/conf/thingsboard.yml**\) to "cassandra" instead of "sql" in order to upgrade your cassandra database:

```text
database:
    type: "${DATABASE_TYPE:cassandra}" # cassandra OR sql
```

#### Start the service

```bash
$ sudo service thingsboard start
```

### Windows

#### ThingsBoard package download

Download ThingsBoard installation archive for Windows: [thingsboard-windows-2.0.2.zip](https://github.com/thingsboard/thingsboard/releases/download/v2.0.2/thingsboard-windows-2.0.2.zip).

#### ThingsBoard service upgrade

* Stop ThingsBoard service if it is running.

```text
net stop thingsboard
```

* Make a backup of previous ThingsBoard configuration located in \\conf \(for ex. C:\thingsboard\conf\).
* Remove ThingsBoard install dir.
* Unzip installation archive to ThingsBoard install dir.
* Compare your old ThingsBoard configuration files \(from the backup you made in the first step\) with new ones.
* Please make sure that you set database.type parameter value \(in the file **\\conf\thingsboard.yml**\) to "cassandra" instead of "sql" in order to upgrade your cassandra database:

  ```text
  database:
      type: "${DATABASE_TYPE:cassandra}" # cassandra OR sql
  ```

#### Start the service

```text
net start thingsboard
```

## Upgrading to 2.0.3

These steps are applicable for 2.0.2 ThingsBoard version.

### Ubuntu/CentOS

#### ThingsBoard package download

#### ThingsBoard service upgrade

**NOTE:** Package installer will ask you to merge your thingsboard configuration. It is preferred to use **merge option** to make sure that all your previous parameters will not be overwritten.  
Please make sure that you set database.type parameter value \(in the file **/etc/thingsboard/conf/thingsboard.yml**\) to "cassandra" instead of "sql" in order to upgrade your cassandra database:

```text
database:
    type: "${DATABASE_TYPE:cassandra}" # cassandra OR sql
```

#### Start the service

```bash
$ sudo service thingsboard start
```

### Windows

#### ThingsBoard package download

Download ThingsBoard installation archive for Windows: [thingsboard-windows-2.0.3.zip](https://github.com/thingsboard/thingsboard/releases/download/v2.0.3/thingsboard-windows-2.0.3.zip).

#### ThingsBoard service upgrade

* Stop ThingsBoard service if it is running.

```text
net stop thingsboard
```

* Make a backup of previous ThingsBoard configuration located in \\conf \(for ex. C:\thingsboard\conf\).
* Remove ThingsBoard install dir.
* Unzip installation archive to ThingsBoard install dir.
* Compare your old ThingsBoard configuration files \(from the backup you made in the first step\) with new ones.
* Please make sure that you set database.type parameter value \(in the file **\\conf\thingsboard.yml**\) to "cassandra" instead of "sql" in order to upgrade your cassandra database:

  ```text
  database:
      type: "${DATABASE_TYPE:cassandra}" # cassandra OR sql
  ```

#### Start the service

```text
net start thingsboard
```

## Upgrading to 2.1.0

These steps are applicable for 2.0.3 ThingsBoard version.

### Ubuntu/CentOS

#### ThingsBoard package download

#### ThingsBoard service upgrade

**NOTE:** Package installer will ask you to merge your thingsboard configuration. It is preferred to use **merge option** to make sure that all your previous parameters will not be overwritten.  
Please make sure that you set database.type parameter value \(in the file **/etc/thingsboard/conf/thingsboard.yml**\) to "cassandra" instead of "sql" in order to upgrade your cassandra database:

```text
database:
    type: "${DATABASE_TYPE:cassandra}" # cassandra OR sql
```

#### Start the service

```bash
$ sudo service thingsboard start
```

### Windows

#### ThingsBoard package download

Download ThingsBoard installation archive for Windows: [thingsboard-windows-2.1.zip](https://github.com/thingsboard/thingsboard/releases/download/v2.1/thingsboard-windows-2.1.zip).

#### ThingsBoard service upgrade

* Stop ThingsBoard service if it is running.

```text
net stop thingsboard
```

* Make a backup of previous ThingsBoard configuration located in \\conf \(for ex. C:\thingsboard\conf\).
* Remove ThingsBoard install dir.
* Unzip installation archive to ThingsBoard install dir.
* Compare your old ThingsBoard configuration files \(from the backup you made in the first step\) with new ones.
* Please make sure that you set database.type parameter value \(in the file **\\conf\thingsboard.yml**\) to "cassandra" instead of "sql" in order to upgrade your cassandra database:

  ```text
  database:
      type: "${DATABASE_TYPE:cassandra}" # cassandra OR sql
  ```

#### Start the service

```text
net start thingsboard
```

## Next steps

