---
layout: docwithnav
assignees:
  - ashvayka
title: Send Mail Action
---

# send-mail-action

## Overview

This component allows building email message by substitution of device attributes and message data into configurable templates.

## Configuration

During action configuration you are able to specify following templates: from, to, cc, bcc, subject and body. The template syntax is based on [Velocity](https://velocity.apache.org/) and is already described in [alarm processor documentation](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/processors/alarm-deduplication-processor/README.md#configuration).

Additionally, you can specify _Send Flag_ property. This is an optional property that may be used in combination with [isNewAlarm](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/processors/alarm-deduplication-processor/README.md#overview) or left blank.

## Example

As a tenant administrator, you are able to review action example inside **Rules-&gt;Demo Alarm Rule-&gt;Actions-&gt;Send Mail Action**.

