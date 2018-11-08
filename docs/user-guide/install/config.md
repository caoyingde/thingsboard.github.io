---
layout: docwithnav
assignees:
  - ashvayka
title: Configuration
description: ThingsBoard IoT platform configuration guide
---

# config

This guide will help you to get familiar with ThingsBoard configuration files and parameters.

Once you have installed ThingsBoard, you can find configuration files in the following directory:

```bash
Windows: YOUR_INSTALL_DIR/conf
Linux: /etc/thingsboard/conf
```

We will describe main configuration files below.

## thingsboard.yml

This is the main configuration file that contains configuration properties for transports \(HTTP, MQTT, CoAP\), database \(Cassandra\), clustering \(Zookeeper and gRPC\), etc. The configuration file is written in YAML.

All configuration parameters have corresponding environment variable name and default value. In order to change configuration parameter you can simply change it's default value. For example:

```bash
server:
  address: "${HTTP_BIND_ADDRESS:0.0.0.0}"
```

In this case, _'HTTP\_BIND\_ADDRESS'_ is environment variable name and _'0.0.0.0'_ is a default value. Environment variables are useful in case of docker installation. See [docker documentation](https://docs.docker.com/compose/environment-variables/#/the-envfile-configuration-option) for more details.

There is **80+** configuration parameters in **thingsboard.yml** file. You can review their description in the [**configuration file**](https://raw.githubusercontent.com/thingsboard/thingsboard/master/application/src/main/resources/thingsboard.yml) itself. We will list only main configuration parameters below to avoid duplication of the parameter descriptions and to simplify maintenance of this documentation page.

| **Property** | **Description** | **Default Value** | **Environment Variable** |
| :--- | :--- | :--- | :--- |
| server.address | HTTP Server bind address | 0.0.0.0 | HTTP\_BIND\_ADDRESS |
| server.port | HTTP Server bind port | 8080 | HTTP\_BIND\_PORT |
| mqtt.bind\_address | MQTT Server bind address | 0.0.0.0 | MQTT\_BIND\_ADDRESS |
| mqtt.bind\_port | MQTT Server bind port | 1883 | MQTT\_BIND\_PORT |
| coap.bind\_address | CoAP Server bind address | 0.0.0.0 | COAP\_BIND\_ADDRESS |
| coap.bind\_port | CoAP Server bind port | 5683 | COAP\_BIND\_PORT |
| cassandra.url | Cassandra node list | 127.0.0.1:9042 | CASSANDRA\_URL |
| security.jwt.tokenExpirationTime | JWT token expiration time in seconds used by Web UI | 900 | JWT\_TOKEN\_EXPIRATION\_TIME |
| security.jwt.refreshTokenExpTime | JWT refresh token expiration time in seconds used by Web UI \(session expiration time\) | 3600 | JWT\_REFRESH\_TOKEN\_EXPIRATION\_TIME |
| database.type | Type of the database to use: sql or cassandra | sql | DATABASE\_TYPE |

## thingsboard.conf

The configuration file for the startup script. Contains Java options and classpath related parameters.

## actor-system.conf

Actor system configuration. Contains general actor system properties and configuration of [Akka dispatchers](http://doc.akka.io/docs/akka/current/java/dispatchers.html). Allows performance tuning for specific use cases.

## logback.xml

The configuration file for logging. Allows controlling the log level, the size of log files and the total size/volume of logs.

