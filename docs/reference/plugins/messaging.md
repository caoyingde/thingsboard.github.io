---
layout: docwithnav
assignees:
  - ashvayka
title: Device Messaging Plugin
---

# messaging

## Overview

This RPC plugin enables communication between various IoT devices through the ThingsBoard cluster. The plugin introduces basic security features: devices are able to exchange messages only if they belong to the same customer. The plugin implementation can be customized to cover more complex security features.

## Configuration

You can specify following configuration parameters:

* Maximum amount of devices per customer
* Default request timeout
* Maximum request timeout 

## Device RPC API

The plugin handles two rpc methods: _getDevices_ and _sendMsg_. The examples listed below will be based on [demo account](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/samples/demo-account/README.md) and [MQTT](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/mqtt-api/README.md#client-side-rpc) protocol. Please note that you are able to use other protocols - [CoAP](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/coap-api/README.md#client-side-rpc) and [HTTP](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/http-api/README.md#client-side-rpc).

### Get Device List API

In order to send a message to other devices, you will need to know their identifiers. A device can request a list of other devices that belong to the same customer using _getDevices_ RPC call.

### Send Message API

A device can send a message to other device that belongs to the same customer using _sendMsg_ RPC call.

The example below will attempt to send a message from device "Test Device A1" to device "Test Device A2".

As a result, you should receive the following error:

```javascript
{"error":"No active connection to the remote device!"}
```

Let's launch emulator of target device and send message again:

As a result, you should receive following response from device:

```javascript
{"status":"ok"}
```

**Note** that target device id, access tokens, request and response bodies are hardcoded into scripts and correspond to the [demo devices](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/samples/demo-account/README.md#tenant-devices).

## Example

As a tenant administrator, you are able to review plugin example inside **Plugins-&gt;Demo Device Messaging RPC Plugin**.

