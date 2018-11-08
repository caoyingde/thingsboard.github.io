---
layout: docwithnav
assignees:
  - ashvayka
title: Installing ThingsBoard on Raspberry Pi 3 Model B
description: Installing ThingsBoard IoT Platform on Raspberry Pi 3 Model B
---

# rpi

* TOC

  {:toc}

This guide describes how to install ThingsBoard on a Raspberry Pi 3 running Raspbian Jessie.

### Third-party components installation

#### Java

ThingsBoard service is running on Java 8. Oracle Java 8 is already pre-installed on Raspbian. You can check java version using the following command

```bash
$ java -version
java version "1.8.0_65"
Java(TM) SE Runtime Environment (build 1.8.0_65-b17)
Java HotSpot(TM) Client VM (build 25.65-b01, mixed mode)
```

Any Java version higher than or equal to 1.8 is fine.

#### \[Optional\] External database installation

**SQL Database: PostgreSQL**

Instructions listed below will help you to install PostgreSQL.

```bash
sudo apt-get update
sudo apt-get install postgresql postgresql-contrib
sudo service postgresql start
```

### ThingsBoard service installation

Download installation package or [build it from source](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/install/building-from-source/README.md).

```bash
# Download the package
$ wget https://github.com/thingsboard/thingsboard/releases/download/v2.1/thingsboard-2.1.deb
# Install ThingsBoard as a service
$ sudo dpkg -i thingsboard-2.1.deb
# Update ThingsBoard memory usage and restrict it to 150MB in /etc/thingsboard/conf/thingsboard.conf
export JAVA_OPTS="$JAVA_OPTS -Dplatform=rpi -Xms256M -Xmx256M"
```

### \[Optional\] Configure ThingsBoard to use PostgreSQL

Edit ThingsBoard configuration file

```bash
sudo nano /etc/thingsboard/conf/thingsboard.yml
```

**NOTE**: Please allow up to 2 minutes for the Web UI to start

### Troubleshooting

ThingsBoard logs are stored in the following directory:

```bash
/var/log/thingsboard
```

You can issue the following command in order to check if there are any errors on the backend side:

```bash
cat /var/log/thingsboard/thingsboard.log | grep ERROR
```

## Next steps

