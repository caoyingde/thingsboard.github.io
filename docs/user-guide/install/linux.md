---
layout: docwithnav
assignees:
  - ashvayka
title: Installing ThingsBoard on Linux
description: Installing ThingsBoard on Linux
---

# linux

* TOC

  {:toc}

This guide describes how to install ThingsBoard on a Linux based server machine. Instructions below are provided for Ubuntu 16.04 and CentOS 7. These instructions can be easily adapted to other similar operating systems.

### Hardware requirements

To run ThingsBoard and third-party components on a single machine you will need at least 1Gb of RAM.

### Third-party components installation

#### Java

ThingsBoard service is running on Java 8. Although you are able to start the service using [OpenJDK](http://openjdk.java.net/), the solution is actively tested on [Oracle JDK](http://www.oracle.com/technetwork/java/javase/overview/index.html).

Follow this instructions to install Oracle JDK 8:

* [Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04#installing-the-oracle-jdk)
* [CentOS 7](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8)

Please don't forget to configure your operating system to use Oracle JDK 8 by default. Corresponding instructions are in the same articles listed above.

#### \[Optional\] External database installation

**SQL Database: PostgreSQL**

Instructions listed below will help you to install PostgreSQL.

**NoSQL Database: Cassandra**

Instructions listed below will help you to install Cassandra.

### ThingsBoard service installation

Download installation package or [build it from source](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/install/building-from-source/README.md).

Install ThingsBoard as a service

### \[Optional\] Configure ThingsBoard to use the external database

Edit ThingsBoard configuration file

```bash
sudo nano /etc/thingsboard/conf/thingsboard.yml
```

For **PostgreSQL**:

For **Cassandra DB**:

Locate and set database type configuration parameter to 'cassandra'.

```text
database:
  type: "${DATABASE_TYPE:cassandra}" # cassandra OR sql
```

For ThingsBoard service:

```bash
# Update ThingsBoard memory usage and restrict it to 256MB in /etc/thingsboard/conf/thingsboard.conf
export JAVA_OPTS="$JAVA_OPTS -Xms256M -Xmx256M"
```

**NOTE**: Please allow up to 90 seconds for the Web UI to start

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

