---
layout: docwithnav
assignees:
  - ashvayka
title: IoT Gateway Configuration
---

# configuration

This guide will help you to get familiar with ThingsBoard IoT Gateway configuration files and parameters.

Once you have installed ThingsBoard IoT Gateway, you can find configuration files in the following directory:

```bash
Linux: /etc/tb-gateway/conf
Windows: $INSTALL_DIR/conf
```

We will describe main configuration files below.

## tb-gateway.yml

The main configuration file that is used to setup connection to ThingsBoard server and enable/disable extensions.

| **Configuration property** | **Description** |
| :--- | :--- |
| **ThingsBoard connection properties** |  |
| gateway.connection.host | ThingsBoard server hostname. For example, demo.thingsboard.io - live demo server. |
| gateway.connection.port | ThingsBoard server MQTT port \(1883 for not encrypted connection, 8883 for encrypted connection\) |
| gateway.connection.retryInterval | ThingsBoard connect retry interval in milliseconds. |
| gateway.connection.maxInFlight | Maximum amount of pending publish messages. Pending messages are messages that are either not sent due to connection problem or not yet confirmed due to high load on ThingsBoard Server. |
| **ThingsBoard security properties** |  |
| gateway.security.accessToken | Populate this field in case of [Access Token based authentication](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/access-token/README.md) |
| gateway.security.keystore | Absolute or relative pass to keystore. Used in case of [X.509 Certificate based authentication](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/certificates/README.md) |
| gateway.security.keystorePassword | Password to the keystore. |
| gateway.security.keystoreKeyAlias | Name of the client key in keystore. Password to the key should match password to keystore. |
| gateway.security.truststore | Absolute or relative pass to truststore. Used in case of encrypted connection. |
| gateway.security.truststorePassword | Password to the truststore. |
| **Misc gateway properties** |  |
| gateway.reporting.interval | Statistics report interval in milliseconds. Reports amount of connected devices and sent messages. |
| gateway.persistence.type | Either "file" or "memory" message persistence options available. |
| gateway.persistence.path | Path to the storage file in case of "file" persistence. Make sure that user who is running gateway process is able to create/modify the file. |
| gateway.persistence.bufferSize | Maximum size of messages in storage. |
| **OPC-UA extension** |  |
| opc.enabled | Either "true" or "false". Boolean flag that enables OPC-UA extension. |
| opc.configuration | Absolute or relative pass to OPC-UA extension configuration file. See the corresponding section for more details. |
| **MQTT extension** |  |
| mqtt.enabled | Either "true" or "false". Boolean flag that enables MQTT extension. |
| mqtt.configuration | Absolute or relative pass to MQTT extension configuration file. See the corresponding section for more details. |
| **Sigfox extension** |  |
| sigfox.enabled | Either "true" or "false". Boolean flag that enables Sigfox extension. |
| sigfox.configuration | Absolute or relative pass to Sigfox extension configuration file. See the corresponding section for more details. |
| **HTTP server properties** |  |
| server.address | HTTP server bind address. Reserved for future usage. |
| server.port | HTTP server bind port. Reserved for future usage |

## logback.xml

Logging configuration file that is based on [Logback](https://logback.qos.ch/) library.

Most important loggers are listed below. Supported log levels: TRACE, DEBUG, INFO, WARN, ERROR

```bash
    <logger name="org.thingsboard" level="INFO" />
    <logger name="org.eclipse.milo" level="INFO" />
    <logger name="org.eclipse.paho" level="INFO" />
```

## OPC-UA Extension

OPC-UA Extension configuration is covered on the corresponding [extension page](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/opc-ua/README.md).

## MQTT Extension

MQTT Extension configuration is covered on the corresponding [extension page](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/mqtt/README.md).

## Sigfox Extension

SIGFOX Extension configuration is covered on the corresponding [extension page](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/sigfox/README.md).

## Modbus Extension

Modbus Extension configuration is covered on the corresponding [extension page](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/modbus/README.md).

## Multi-tenant configuration

Multi-tenant configuration is covered on the corresponding [**multi-tenant configuration page**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/multi-tenant-configuration/README.md)

