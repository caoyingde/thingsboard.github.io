---
layout: docwithnav
assignees:
  - ashvayka
title: RabbitMQ Plugin
---

# rabbitmq

## Overview

RabbitMQ plugin is responsible for sending messages to RabbitMQ instances triggered by specific rules

## Configuration

You can specify following configuration parameters:

* rabbitmq instance host
* rabbitmq instance port
* rabbitmq virtual host
* username for authorization
* password for authorization
* enables automation connection revovery in case of failure
* connection timeout
* handshake timeout
* additional client properties that could be usefull for connecting to specific rabbitmq instances

## Server-side API

This plugin does not provide any server-side API.

## Example

In this example, we are going to demonstrate how you can configure RabbitMQ extension to be able to send messages to particular queue every time new telemetry message for the device arrives.

Prerequisites before continuing RabbitMQ extension configuration:

* ThingsBoard is up and running
* RabbitMQ instance is up and running

### RabbitMQ Plugin Configuration

Let's configure RabbitMQ plugin first. Go to _Plugins_ menu, click on a '+' button and create new plugin:

![image](../../../.gitbook/assets/rabbitmq-plugin-config-1.png)

![image](../../../.gitbook/assets/rabbitmq-plugin-config-2.png)

Please set host, port and credentials correctly so extension is able to connect to RabbitMQ broker.

Save plugin and click on _'Activate'_ plugin button:

![image](../../../.gitbook/assets/rabbitmq-activate-plugin.png)

### RabbitMQ Rule Configuration

Now it's time to create appropriate Rule.

![image](../../../.gitbook/assets/rabbitmq-rule-config.png)

Add filter for **POST\_TELEMETRY** message type:

![image](../../../.gitbook/assets/post-telemetry-filter%20%281%29.png)

Click _'Add'_ button to add the filter.

Then select _'RabbitMQ Plugin'_ in the drop-down box for the Plugin field:

![image](../../../.gitbook/assets/rabbitmq-plugin-selection.png)

Add action that will send temperature telemetry of device to particular RabbitMQ queue:

![image](../../../.gitbook/assets/rabbitmq-rule-action-config.png)

Click _'Add'_ button and then activate Rule.

### Sending Temperature Telemetry

Now for any of your devices send Telemetry message that contains _'temp'_ telemetry:

```javascript
{"temp":73.4}
```

You should receive message **'73.4'** in appropriate RabbitMQ queue once you'll post this message.

Here is an example of a command that publish single telemetry message to locally installed ThingsBoard:

```bash
mosquitto_pub -d -h "localhost" -p 1883 -t "v1/devices/me/telemetry" -u "$ACCESS_TOKEN" -m '{"temp":73.4}'
```

