---
layout: docwithnav
assignees:
  - ashvayka
title: Using RPC capabilities
description: Remote control of IoT devices from the ThingsBoard IoT cloud using RPC feature
---

# rpc

* TOC

  {:toc}

ThingsBoard allows you to send remote procedure calls \(RPC\) from server side applications to devices and vice versa. Basically, this feature allows you to send commands to devices and receive results of commands execution. Similar, you can execute request from the device, apply some calculations or other server-side logic on the back-end and push the response back to the device. This guide covers ThingsBoard RPC capabilities. After reading this guide, you will get familiar with following topics:

* RPC call types
* Basic RPC use-cases
* RPC client-side and server-side APIs
* RPC widgets

## RPC call types

Thinsboard RPC feature can be divided into two types based on originator: device-originated and server-originated RPC calls. In order to use more familiar names, we will name device-originated RPC calls as a **client-side** RPC calls and server-originated RPC calls as **server-side** RPC calls.

{:refdef: style="text-align: center;"} ![image](../../.gitbook/assets/client-side-rpc.svg) {: refdef}

Server-side RPC calls can be divided into one-way and two-way:

* One-way RPC request is sent to the device without delivery confirmation and obviously, does not provide any response from the device. RPC call may fail only if there is no active connection with the target device within a configurable timeout period.

  {:refdef: style="text-align: center;"} ![image](../../.gitbook/assets/one-way-rpc.svg) {: refdef}

* Two-way RPC request is sent to the device and expects to receive a response from the device within the certain timeout. The Server-side request is blocked until the target device replies to the request.

  {:refdef: style="text-align: center;"} ![image](../../.gitbook/assets/two-way-rpc.svg) {: refdef}

## Device RPC API

ThingsBoard provides convenient API to send and receive RPC commands from applications running on the device. This API is specific for each supported network protocol. You can review API and examples in corresponding reference page:

* [MQTT RPC API reference](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/mqtt-api/README.md#rpc-api)
* [CoAP RPC API reference](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/coap-api/README.md#rpc-api)
* [HTTP RPC API reference](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/http-api/README.md#rpc-api) 

## Server-side RPC API

ThingsBoard provides **System RPC Service** that allows you to send RPC calls from server-side applications to the device. In order to send RPC request you need execute HTTP POST request to the following URL:

```text
http(s)://host:port/api/plugins/rpc/{callType}/{deviceId}
```

where

* **callType** is either **oneway** or **twoway**
* **deviceId** is your target [device id](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/ui/devices/README.md#get-device-id)

The request body should be a valid json object with two elements:

* **method** - method name, json string
* **params** - method parameters, json object

For example:

Please **note** that in order to execute this request, you will need to substitute **$JWT\_TOKEN** with a valid JWT token. This token should belong to either

* user with **TENANT\_ADMIN** role
* user with **CUSTOMER\_USER** role that owns the device identified by **$DEVICE\_ID**

You can use following [guide](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/rest-api/README.md#rest-api-auth) to get the token.

## RPC Rule Nodes

It is possible to integrate RPC actions into processing workflow. There are 2 Rule Nodes for working with RPC requests.

* [RPC reply](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rule-engine-2-0/action-nodes/README.md#rpc-call-reply-node) 
* [RPC request](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rule-engine-2-0/action-nodes/README.md#rpc-call-request-node) 

## RPC widgets

See [widgets library](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/ui/widget-library/README.md#gpio-widgets) for more details.

