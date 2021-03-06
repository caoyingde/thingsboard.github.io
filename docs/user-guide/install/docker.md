---
layout: docwithnav
assignees:
  - ashvayka
title: Installing ThingsBoard using Docker (Linux or Mac OS)
description: Installing ThingsBoard IoT Platform using Docker (Linux or Mac OS)
---

# docker

* TOC

  {:toc}

This guide will help you to install and start ThingsBoard using Docker on Linux or Mac OS.

## Installation steps

* [Install Docker](https://docs.docker.com/engine/installation/)
* [Install Docker Compose \(Linux only\)](https://docs.docker.com/compose/install/) - Mac OS Docker installation already contains Docker Compose.
* If you have already installed ThingsBoard using docker and want to upgrade or cleanup your installation, please cleanup HSQLDB data directory

```bash
sudo rm -rf /home/docker/hsqldb_volume
```

* Once started, you will be able to open Web UI using following link:

```bash
http://localhost:8080/
```

## Advanced usage

### .env file

One can modify **.env** file to configure following parameters:

* CASSANDRA\_DATA\_DIR - location of cassandra data folder on host machine
* POSTGRES\_DATA\_DIR - location of postgres data folder on host machine
* HSQLDB\_DATA\_DIR - location of hsqldb data folder on host machine
* ADD\_SCHEMA\_AND\_SYSTEM\_DATA - create schema and add system user and rule chains. by default _false_
* ADD\_DEMO\_DATA - add demo accounts, dashboards and devices. by default _false_
* CASSANDRA\_URL - url of cassandra container 

### tb.env file

One can set thingsboard service environment variables using this file. See [configuration](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/install/config/README.md#thingsboardyml) for more details.

## Troubleshooting

### DNS issues

**Note** If you observe errors related to DNS issues, for example

```bash
127.0.1.1:53: cannot unmarshal DNS message
```

You may configure your system to use Google public DNS servers. See corresponding [Linux](https://developers.google.com/speed/public-dns/docs/using#linux) and [Mac OS](https://developers.google.com/speed/public-dns/docs/using#mac_os) instructions.

## Next steps

