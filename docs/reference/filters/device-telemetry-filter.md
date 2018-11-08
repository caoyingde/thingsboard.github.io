---
layout: docwithnav
assignees:
  - ashvayka
title: Device Telemetry Filter
---

# device-telemetry-filter

## Overview

This component allows filtering incoming [telemetry](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/telemetry/README.md) messages by their values. This filter is very useful if you want to apply rule based on certain values of telemetry. For example, an engine controller may periodically report its temperature. When engine temperature is higher than 100 degrees you may raise an alert. The filter expression is written in javascript.

## Configuration

You are able to write boolean javascript expression using bindings that match keys of your telemetry message. If you are not sure that certain key is present in your message, you can add check it's type for _undefined_. For example, filter below will match if _temperature_ is higher then _100_ degrees.

```javascript
typeof temperature !== 'undefined' && temperature > 100
```

Assuming following telemetry message uploaded from engine controller device:

```javascript
{"temperature":1100, "enabled":true, "mode":"A"}
```

The following filter will match if device is enabled, operating in mode 'A' and temperature is greater than 1000 degrees

```javascript
temperature > 1000 && enabled == true && mode == 'A'
```

If you are not sure that all telemetry data points are present in the message, you should use the following syntax that adds all necessary "null" checks

```javascript
typeof temperature!== 'undefined' && typeof enabled !== 'undefined' && typeof mode !== 'undefined' && 
temperature > 1000 && enabled == true && mode == 'A'
```

## Example

As a tenant administrator, you are able to review filter example inside **Rules-&gt;Demo Alarm Rule-&gt;Filters-&gt;Device Telemetry Filter**.

