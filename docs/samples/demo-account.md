---
layout: docwithnav
assignees:
  - ashvayka
title: Demo Account
description: ThingsBoard default demo accounts
---

# demo-account

* TOC

  {:toc}

ThingsBoard installation contains single tenant account that is used in sample applications and contains a lot of pre-provisioned entities for demonstration purposes.

## System Administrator

Default system administrator account:

* login - **sysadmin@thingsboard.org**.
* password - **sysadmin**.

## Demo Tenant

Default tenant administrator account:

* login - **tenant@thingsboard.org**.
* password - **tenant**.

Demo tenant customers:

* Customer A users -  **customer@thingsboard.org** or **customerA@thingsboard.org**.
* Customer B users -  **customerB@thingsboard.org**.
* Customer C users -  **customerC@thingsboard.org**.
* all users have **"customer"** password. 

## Tenant devices

* Test Device A1, A2, A3 - belong to Customer A. Access tokens: A1\_TEST\_TOKEN, A2\_TEST\_TOKEN and A3\_TEST\_TOKEN.
* Test Device B1 - belong to Customer B. Access token: B1\_TEST\_TOKEN.
* Test Device C1 - belong to Customer C. Access token: C1\_TEST\_TOKEN.
* DHT11 Demo Device - created for temperature and humidity upload [sample applications](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/samples/nodemcu/temperature/README.md). Access token: DHT11\_DEMO\_TOKEN
* Raspberry Pi Demo Device - created for GPIO control [sample application](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/samples/raspberry/gpio/README.md).

  Access token: RASPBERRY\_PI\_DEMO\_TOKEN

## Dashboards

* Temperature & Humidity Demo Dashboard - created for temperature and humidity upload [sample applications](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/samples/nodemcu/temperature/README.md).
* Raspberry PI GPIO Demo Dashboard - created for Raspberry Pi GPIO control [sample application](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/samples/raspberry/gpio/README.md).

## Rule Chains

There is predefined Rule Chain for storing all incoming telemetry and attribute updates. All other incoming requests just logged. For adding additional Rule Nodes, like Send Email, Create Alarms, etc. please read related articles:

* [Rule Engine Getting Started](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rule-engine-2-0/re-getting-started/README.md)
* [Rule Engine Overview](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rule-engine-2-0/overview/README.md)
* [Rule Engine Tutorials](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rule-engine-2-0/overview/README.md#tutorials)

