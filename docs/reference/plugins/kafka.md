---
layout: docwithnav
assignees:
  - ashvayka
title: Kafka Plugin
---

# kafka

## Overview

Kafka plugin is responsible for sending messages to Kafka brokers triggered by specific rules

## Configuration

You can specify following configuration parameters:

* _bootstrap servers_ - list of kafka brokers
* _number of attempts to reconnect to kafka if connection fails_
* _number of messages to unit into batch on client_
* _time to buffer locally before sending to kafka broker \(in ms\)_
* _buffer max size on client_
* _minimum number of replicas that must acknowledge a write_
* _topic key serializer_ by default - org.apache.kafka.common.serialization.StringSerializer
* _topic value serializer_ by default - org.apache.kafka.common.serialization.StringSerializer
* any other additional properties could be provided for kafka broker connection

## Server-side API

This plugin does not provide any server-side API.

## Example

In this example, we are going to demonstrate how you can configure this extension to be able to send a message to Kafka topic every time new telemetry message for the device arrives.

Prerequisites before contining Kafka extension configuration:

* Kafka broker is up and running
* Appropriate Kafka Topic created
* ThingsBoard is up and running

### Kafka Plugin Configuration

Let's configure Kafka plugin first. Go to _Plugins_ menu and create new plugin:

![image](../../../.gitbook/assets/kafka-plugin-config-1.png)

![image](../../../.gitbook/assets/kafka-plugin-config-2.png)

Please set correctly Kafka Bootstrap Servers URL and any other parameters located in plugin configuration section that is suitable for your case so Kafka extension is able to connect to Kafka broker.

Click on _'Activate'_ plugin button:

![image](../../../.gitbook/assets/kafka-activate-plugin.png)

### Kafka Rule Configuration

Now it's time to create appropriate Rule.

![image](../../../.gitbook/assets/kafka-rule-config.png)

Add filter for **POST\_TELEMETRY** message type:

![image](../../../.gitbook/assets/post-telemetry-filter%20%282%29.png)

Click _'Add'_ button to add filter.

Then select _'Kafka Plugin'_ in the drop-down box for the Plugin field:

![image](../../../.gitbook/assets/kafka-plugin-selection.png)

Add action that will send temperature telemetry of device to particular kafka topic:

![image](../../../.gitbook/assets/send-temp-telemetry.png)

Click _'Add'_ button and then activate Rule.

### Sending Temperature Telemetry

Now you can send Telemetry message that contains _'temp'_ telemetry for any of your devices:

```javascript
{"temp":73.4}
```

You should see **'73.4'** message in appropriate Kafka topic once you'll post this message.

Here is an example of a command that publish single telemetry message to locally installed ThingsBoard:

```bash
mosquitto_pub -d -h "localhost" -p 1883 -t "v1/devices/me/telemetry" -u "$ACCESS_TOKEN" -m '{"temp":73.4}'
```

