---
layout: docwithnav
assignees:
  - ashvayka
title: Time RPC Plugin
---

# time

## Overview

Simple RPC plugin that is responsible for handling "getTime" RPC request from devices. This plugin is a part of default ThingsBoard installation for demo purposes. It demonstrates that devices can send RPC request via various [connectivity protocols](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/protocols/README.md) to execute server-side logic and get the result.

## Configuration

You can specify _time format_ configuration parameter. See [DateTimeFormatter API](https://docs.oracle.com/javase/8/docs/api/java/time/format/DateTimeFormatter.html) for more details.

## Server-side API

This plugin does not provide any server-side API.

## Example

As a tenant administrator, you are able to review plugin example inside **Plugins-&gt;Demo Time RPC Plugin**.

