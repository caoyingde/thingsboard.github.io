---
layout: docwithnav
assignees:
  - ikulikov
title: Upgrade instructions
---

# upgrade-instructions

*  [Upgrading to 1.1.0](upgrade-instructions.md#upgrading-to-110)
  *  [Ubuntu/CentOS](upgrade-instructions.md#ubuntucentos)
  *  [Windows](upgrade-instructions.md#windows)
*  [Upgrading to 1.2.0](upgrade-instructions.md#upgrading-to-120)
  *  [Ubuntu/CentOS](upgrade-instructions.md#ubuntucentos-1)
  *  [Windows](upgrade-instructions.md#windows-1)
*  [Upgrading to 1.2.1](upgrade-instructions.md#upgrading-to-121)
  *  [Ubuntu/CentOS](upgrade-instructions.md#ubuntucentos-2)
  *  [Windows](upgrade-instructions.md#windows-2)

## Upgrading to 1.1.0

These steps are applicable for 1.0.0 IoT Gateway version.

### Ubuntu/CentOS

#### Gateway package download

#### Gateway service upgrade

#### Start the service

```bash
$ sudo service tb-gateway start
```

### Windows

#### Gateway package download

Download Gateway installation archive for Windows: [tb-gateway-windows-1.1.zip](https://github.com/thingsboard/thingsboard-gateway/releases/download/v1.1/tb-gateway-windows-1.1.zip).

#### Gateway service upgrade

* Make a backup of previous Gateway configuration located in \\conf \(for ex. C:\tb-gateway\conf\).
* Uninstall the previous version of Gateway service by running **uninstall.bat** located in Gateway install dir.

**NOTE** Scripts listed above should be executed using Administrator Role.

```text
C:\tb-gateway>uninstall.bat
```

* Remove Gateway install dir.
* Unzip installation archive to Gateway install dir.
* Compare your old Gateway configuration files \(from the backup you made in the first step\) with new ones.
* Run **install.bat** script to install the new version of Gateway as a Windows service.

```text
C:\tb-gateway>install.bat
```

#### Start the service

```text
net start tb-gateway
```

## Upgrading to 1.2.0

These steps are applicable for 1.1.0 IoT Gateway version.

### Ubuntu/CentOS

#### Gateway package download

#### Gateway service upgrade

#### Start the service

```bash
$ sudo service tb-gateway start
```

### Windows

#### Gateway package download

Download Gateway installation archive for Windows: [tb-gateway-windows-1.2.zip](https://github.com/thingsboard/thingsboard-gateway/releases/download/v1.2/tb-gateway-windows-1.2.zip).

#### Gateway service upgrade

* Make a backup of previous Gateway configuration located in \\conf \(for ex. C:\tb-gateway\conf\).
* Uninstall the previous version of Gateway service by running **uninstall.bat** located in Gateway install dir.

**NOTE** Scripts listed above should be executed using Administrator Role.

```text
C:\tb-gateway>uninstall.bat
```

* Remove Gateway install dir.
* Unzip installation archive to Gateway install dir.
* Compare your old Gateway configuration files \(from the backup you made in the first step\) with new ones.
* Run **install.bat** script to install the new version of Gateway as a Windows service.

```text
C:\tb-gateway>install.bat
```

#### Start the service

```text
net start tb-gateway
```

## Upgrading to 1.2.1

These steps are applicable for 1.2.0 IoT Gateway version.

### Ubuntu/CentOS

#### Gateway package download

#### Gateway service upgrade

#### Start the service

```bash
$ sudo service tb-gateway start
```

### Windows

#### Gateway package download

Download Gateway installation archive for Windows: [tb-gateway-windows-1.2.1.zip](https://github.com/thingsboard/thingsboard-gateway/releases/download/v1.2.1/tb-gateway-windows-1.2.1.zip).

#### Gateway service upgrade

* Make a backup of previous Gateway configuration located in \\conf \(for ex. C:\tb-gateway\conf\).
* Uninstall the previous version of Gateway service by running **uninstall.bat** located in Gateway install dir.

**NOTE** Scripts listed above should be executed using Administrator Role.

```text
C:\tb-gateway>uninstall.bat
```

* Remove Gateway install dir.
* Unzip installation archive to Gateway install dir.
* Compare your old Gateway configuration files \(from the backup you made in the first step\) with new ones.
* Run **install.bat** script to install the new version of Gateway as a Windows service.

```text
C:\tb-gateway>install.bat
```

#### Start the service

```text
net start tb-gateway
```

