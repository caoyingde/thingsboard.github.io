---
layout: docwithnav
assignees:
  - ashvayka
title: Working with IoT device alarms
description: IoT device alarm management using ThingsBoard alarms feature
---

# alarms

* TOC

  {:toc}

ThingsBoard provides the ability to create and manage alarms related to your entities: devices, assets, customers, etc.

## Alarm Lifecycle

Alarms have a lifecycle. Each Alarm can be cleared and acknowledged. By default, an alarm is not in the active and unacknowledged state.

## Alarm Originator, Type, and Propagation

Alarm Originator is an entity that is responsible for triggering an alarm. By default, an alarm is propagated to all related entities \(parent relations only\). An alarm is identified by start time, originator and type. There can't be two active alarms for a same type and originator.

## Alarm Severity

One of the following alarm severities is supported: CRITICAL, MAJOR, MINOR, WARNING, INDETERMINATE.

## Alarm Updates

Alarm entity may be updated by external applications or ThingsBoard rules. Alarm keeps track of both clear and acknowledge time and latest change as an end time.

## Alarm REST API

ThingsBoard provides REST API to manage and query alarms. See demo environment [Alarm REST API](https://demo.thingsboard.io/swagger-ui.html#/alarm-controller) and general [REST API](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/rest-api/README.md) documentation for more details.

## Alarm Rules

It is possible to create, update and clear alarm using ThingsBoard [rule engine](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rule-engine-2-0/re-getting-started/README.md).

Please find more details about Alarm Rule Nodes:

* [Create Alarm](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rule-engine-2-0/action-nodes/README.md#create-alarm-node).
* [Clear Alarm](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rule-engine-2-0/action-nodes/README.md#clear-alarm-node).

Also, in this step-by-step guide you can see how to create/update/clear Alarms in real-life scenarios:

* [Work with Alarms](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rule-engine-2-0/tutorials/create-clear-alarms/README.md).

