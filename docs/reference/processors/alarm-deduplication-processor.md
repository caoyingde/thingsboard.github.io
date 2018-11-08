---
layout: docwithnav
assignees:
  - ashvayka
title: Alarm Deduplication Processor
---

# alarm-deduplication-processor

## Overview

This component allows generating unique alarms. You are able to specify _alarm ID_ and _alarm body_ templates. Template evaluation is based on [velocity engine](http://velocity.apache.org/). When component process incoming device messages it substitutes message values and device attributes into template. Alarm uniqueness is controlled by result value of _alarm ID_. If processor detects unique alarm, it will add following metadata:

* _isNewAlarm_ boolean flag to _true_.
* _alarmId_ string.
* _alarmBody_ string.

## Configuration

Template evaluation is done using certain context. This context is populated with values based on device message and attributes. Attribute values are available using maps with following names:

* **cs** - client-side attributes map.
* **ss** - server-side attributes map.
* **shared** - shared attributes map.

Telemetry values are pushed directly to the context using their keys. You can also use _date_, _deviceId_, _deviceName_, and _deviceType_.

For example, following template:

```javascript
[$date.get('yyyy-MM-dd HH:mm:ss')] Device $deviceType+$cs.get('serialNumber')($cs.get('model')) temperature is $temperature.valueAsString!
```

Will be evaluated into

```text
[2016-01-02 03:04:05] Device Killbot4000+SN-001(A) temperature is 100!
```

for Device with

* client-side attribute _serial number_ = SN-001
* client-side attribute _model_ = A

and telemetry message

```javascript
{"temperature":100}
```

We recommend to include the truncated date and some unique device attribute into alarm id template. This will ensure that you will not generate alarms for the same device problem too often.

## Example

As a tenant administrator, you are able to review processor example inside **Rules-&gt;Demo Alarm Rule-&gt;Processors-&gt;Alarm Deduplication Processor**.

