---
layout: docwithnav
assignees:
  - ashvayka
title: HTTP Device API Reference
description: Supported HTTP API Reference for IoT Devices
---

# http-api

* TOC

  {:toc}

## Getting started

#### HTTP basics

[HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol) is a general-purpose network protocol that can be used in IoT applications. You can find more information about HTTP [here](https://www.w3.org/Protocols/rfc2616/rfc2616.txt). HTTP protocol is TCP based and uses request-response model.

ThingsBoard server nodes act as an HTTP Server that supports both HTTP and HTTPS protocols.

#### Client libraries setup

You can find HTTP client libraries for different programming languages on the web. Examples in this article will be based on [curl](https://en.wikipedia.org/wiki/CURL). In order to setup this tool, you can use instructions in our [Hello World](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/getting-started-guides/helloworld/README.md) guide.

#### HTTP Authentication and error codes

We will use _access token_ device credentials in this article and they will be referred to later as **$ACCESS\_TOKEN**. The application needs to include **$ACCESS\_TOKEN** as a path parameter in each HTTP request. Possible error codes and their reasons:

* **400 Bad Request** - Invalid URL, request parameters or body.
* **401 Unauthorized** - Invalid **$ACCESS\_TOKEN**.
* **404 Not Found** - Resource not found.

## Key-value format

By default, ThingsBoard supports key-value content in JSON. Key is always a string, while value can be either string, boolean, double or long. Using custom binary format or some serialization framework is also possible. See [protocol customization](http-api.md#protocol-customization) for more details. For example:

```javascript
{"stringKey":"value1", "booleanKey":true, "doubleKey":42.0, "longKey":73}
```

## Telemetry upload API

In order to publish telemetry data to ThingsBoard server node, send POST request to the following URL:

```text
http(s)://host:port/api/v1/$ACCESS_TOKEN/telemetry
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

In order to publish client-side device attributes to ThingsBoard server node, send POST request to the following URL:

```text
http(s)://host:port/api/v1/$ACCESS_TOKEN/attributes
```

#### Request attribute values from the server

In order to request client-side or shared device attributes to ThingsBoard server node, send GET request to the following URL:

```text
http(s)://host:port/api/v1/$ACCESS_TOKEN/attributes?clientKeys=attribute1,attribute2&sharedKeys=shared1,shared2
```

**Please note**, the intersection of client-side and shared device attribute keys is a bad practice! However, it is still possible to have same keys for client, shared or even server-side attributes.

#### Subscribe to attribute updates from the server

In order to subscribe to shared device attribute changes, send GET request with optional "timeout" request parameter to the following URL:

```text
http(s)://host:port/api/v1/$ACCESS_TOKEN/attributes/updates
```

Once shared attribute will be changed by one of the server-side components \(REST API or Rule Chain\) the client will receive the following update:

## RPC API

### Server-side RPC

In order to subscribe to RPC commands from the server, send GET request with optional "timeout" request parameter to the following URL:

```text
http(s)://host:port/api/v1/$ACCESS_TOKEN/rpc
```

Once subscribed, a client may receive rpc request or a timeout message if there are no requests to a particular device. An example of RPC request body is shown below:

```javascript
{
  "id": "1",
  "method": "setGpio",
  "params": {
    "pin": "23",
    "value": 1
  }
}
```

where

* **id** - request id, integer request identifier
* **method** - RPC method name, string
* **params** - RPC method params, custom json object 

and can reply to them using POST request to the following URL:

```text
http://host:port/api/v1/$ACCESS_TOKEN/rpc/{$id}
```

where **$id** is an integer request identifier.

### Client-side RPC

In order to send RPC commands to the server, send POST request to the following URL:

```text
http://host:port/api/v1/$ACCESS_TOKEN/rpc
```

Both request and response body should be valid JSON documents. Theh content of the documents is specific to the rule node that will handle your request.

## Protocol customization

HTTP transport can be fully customized for specific use-case by changing the corresponding [module](https://github.com/thingsboard/thingsboard/tree/master/transport/http).

## Next steps

