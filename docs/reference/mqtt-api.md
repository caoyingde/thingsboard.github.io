---
layout: docwithnav
assignees:
  - ashvayka
title: MQTT Device API Reference
description: Supported MQTT API Reference for IoT Devices
---

# mqtt-api

* TOC

  {:toc}

## Getting started

#### MQTT basics

[MQTT](https://en.wikipedia.org/wiki/MQTT) is a lightweight publish-subscribe messaging protocol which probably makes it the most suitable for various IoT devices. You can find more information about MQTT [here](http://mqtt.org/).

ThingsBoard server nodes act as an MQTT Broker that supports QoS levels 0 \(at most once\) and 1 \(at least once\) and a set of predefined topics.

#### Client libraries setup

You can find a large number of MQTT client libraries on the web. Examples in this article will be based on Mosquitto and MQTT.js. In order to setup one of those tools, you can use instructions in our [Hello World](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/getting-started-guides/helloworld/README.md) guide.

#### MQTT Connect

We will use _access token_ device credentials in this article and they will be referred to later as **$ACCESS\_TOKEN**. The application needs to send MQTT CONNECT message with username that contains **$ACCESS\_TOKEN**. Possible return codes and their reasons during connect sequence:

* **0x00 Connected** - Successfully connected to ThingsBoard MQTT server.
* **0x04 Connection Refused, bad user name or password** - Username is empty.
* **0x05 Connection Refused, not authorized** - Username contains invalid **$ACCESS\_TOKEN**. 

## Key-value format

By default, ThingsBoard supports key-value content in JSON. Key is always a string, while value can be either string, boolean, double or long. Using custom binary format or some serialization framework is also possible. See [protocol customization](mqtt-api.md#protocol-customization) for more details. For example:

```javascript
{"stringKey":"value1", "booleanKey":true, "doubleKey":42.0, "longKey":73}
```

## Telemetry upload API

In order to publish telemetry data to ThingsBoard server node, send PUBLISH message to the following topic:

```text
v1/devices/me/telemetry
```

The simplest supported data formats are:

```javascript
{"key1":"value1", "key2":"value2"}
```

or

```javascript
[{"key1":"value1"}, {"key2":"value2"}]
```

**Please note** that in this case, the server-side timestamp will be assigned to uploaded data!

In case your device is able to get the client-side timestamp, you can use following format:

```javascript
{"ts":1451649600512, "values":{"key1":"value1", "key2":"value2"}}
```

In the example above, we assume that "1451649600512" is a [unix timestamp](https://en.wikipedia.org/wiki/Unix_time) with milliseconds precision. For example, the value '1451649600512' corresponds to 'Fri, 01 Jan 2016 12:00:00.512 GMT'

## Attributes API

ThingsBoard attributes API allows devices to

* Upload [client-side](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/attributes/README.md#attribute-types) device attributes to the server.
* Request [client-side](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/attributes/README.md#attribute-types) and [shared](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/attributes/README.md#attribute-types) device attributes from the server.
* Subscribe to [shared](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/attributes/README.md#attribute-types) device attributes from the server.

#### Publish attribute update to the server

In order to publish client-side device attributes to ThingsBoard server node, send PUBLISH message to the following topic:

```text
v1/devices/me/attributes
```

#### Request attribute values from the server

In order to request client-side or shared device attributes to ThingsBoard server node, send PUBLISH message to the following topic:

```text
v1/devices/me/attributes/request/$request_id
```

where **$request\_id** is your integer request identifier. Before sending PUBLISH message with the request, client need to subscribe to

```text
v1/devices/me/attributes/response/+
```

The following example is written in javascript and is based on mqtt.js. Pure command-line examples are not available because subscribe and publish need to happen in the same mqtt session.

**Please note**, the intersection of client-side and shared device attribute keys is a bad practice! However, it is still possible to have same keys for client, shared or even server-side attributes.

#### Subscribe to attribute updates from the server

In order to subscribe to shared device attribute changes, send SUBSCRIBE message to the following topic:

```text
v1/devices/me/attributes
```

When a shared attribute is changed by one of the server-side components \(such as the REST API or the Rule Chain\), the client will receive the following update:

```javascript
{"key1":"value1"}
```

## RPC API

### Server-side RPC

In order to subscribe to RPC commands from the server, send SUBSCRIBE message to the following topic:

```text
v1/devices/me/rpc/request/+
```

Once subscribed, the client will receive individual commands as a PUBLISH message to the corresponding topic:

```text
v1/devices/me/rpc/request/$request_id
```

where **$request\_id** is an integer request identifier.

The client should publish the response to the following topic:

```text
v1/devices/me/rpc/response/$request_id
```

The following example is written in javascript and is based on mqtt.js. Pure command-line examples are not available because subscribe and publish need to happen in the same mqtt session.

### Client-side RPC

In order to send RPC commands to server, send PUBLISH message to the following topic:

```text
v1/devices/me/rpc/request/$request_id
```

where **$request\_id** is an integer request identifier. The response from server will be published to the following topic:

```text
v1/devices/me/rpc/response/$request_id
```

The following example is written in javascript and is based on mqtt.js. Pure command-line examples are not available because subscribe and publish need to happen in the same mqtt session.

## Protocol customization

MQTT transport can be fully customized for specific use-case by changing the corresponding [module](https://github.com/thingsboard/thingsboard/tree/master/transport/mqtt).

## Next steps

