---
layout: docwithnav
assignees:
  - ashvayka
title: Mail Plugin
---

# mail

## Overview

Mail plugin is responsible for sending email messages that are triggered by corresponding rule [actions](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/actions/send-mail-action/README.md).

## Configuration

You can specify following parameters:

* mail server host
* mail server port
* user name
* password
* map with other properties. 

  See [java mail sender](http://docs.spring.io/spring/docs/current/javadoc-api/org/springframework/mail/javamail/JavaMailSenderImpl.html#setJavaMailProperties-java.util.Properties-) for more details. 

## Server-side API

This plugin does not provide any server-side API.

## Example

As a tenant administrator, you are able to review plugin example inside **Plugins-&gt;Demo Email Plugin** that is configured to Gmail server. You may want to update username and password to match existing account and start receiving emails.

