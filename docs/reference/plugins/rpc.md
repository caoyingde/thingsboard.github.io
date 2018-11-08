---
layout: docwithnav
assignees:
  - ashvayka
title: RPC Plugin
---

# rpc

## Overview

RPC plugin is responsible for:

* providing REST API to send RPC request from server-side applications to devices;
* pushing RPC request to devices via one of available protocols: 

  [MQTT](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/mqtt-api/README.md#rpc-api), [CoAP](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/coap-api/README.md#rpc-api) or [HTTP](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/http-api/README.md#rpc-api);  

By default, this plugin is configured on the system level by a system administrator. You are able to configure your own instance of the plugin on tenant level. Advanced users or platform developers can customize rpc plugin functionality.

## Configuration

You can specify default RPC timeout for plugin instance in the plugin configuration.

## Server-side API

RPC plugin API description is available in corresponding [rpc](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rpc/README.md#server-side-rpc-api) guides.

## Example

As a system administrator, you are able to review plugin example inside **Plugins-&gt;System RPC Plugin**.

