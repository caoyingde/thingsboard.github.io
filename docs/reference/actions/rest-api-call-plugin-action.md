---
layout: docwithnav
assignees:
  - ashvayka
title: REST API Call Plugin Action
---

# rest-api-call-plugin-action

## Overview

This component allows creating a POST/PUT request body by substitution of device attributes and message data into configurable templates.

## Configuration

During action configuration you are able to specify following:

* set flag to confirm  delivery
* action path of the http endpoint
* request method - POST or PUT
* expected result code in http response
* body template of the request

  The Body Template syntax is based on [Velocity](https://velocity.apache.org/)

  and is already described in [alarm processor documentation](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/processors/alarm-deduplication-processor/README.md#configuration).

## Example

