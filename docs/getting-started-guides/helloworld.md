---
layout: docwithnav
assignees:
  - ashvayka
title: Getting Started
description: >-
  Getting started with ThingsBoard open-source IoT platform and simulated IoT
  devices
---

# helloworld

* TOC

  {:toc}

## Introduction

The goal of this tutorial is to demonstrate the basic usage of the most popular ThingsBoard features. You will learn how to:

* Provision Assets and Devices in the system;
* Define relations between Assets and Devices;
* Push data from a device to ThingsBoard;
* Build real-time end-user Dashboards;
* Define thresholds and trigger alarms;
* Push notification about new alarms over email.

The tutorial is based on a popular facility monitoring use-case. We will show how to monitor temperature in a different parts of the building, raise alarms when temperature exceeds certain threshold and visualize collected data and alarms.

## Video tutorial

We recommend you to review the following video tutorial. All the resources used in this tutorial are listed below for your convenience.

## Tutorial resources

### Live Demo and the installation guides

If you don't have access to a running ThingsBoard instance, use either [Live Demo](https://demo.thingsboard.io/signup) or [Installation Guide](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/install/installation-options/README.md) to fix this.

In case you decided to install your own ThingsBoard server and loaded the demo data \( "--loadDemo" option, according to the installation guides\), the list of default accounts \(login/password\) and device credentials is located [here](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/samples/demo-account/README.md).

### Pushing data from the device

In order to simplify this guide, we will push data using HTTP, MQTT or CoAP protocol from your local PC. Please review [connect your device](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/guides/README.md#AnchorIDConnectYourDevice) guides for all available connectivity solutions and options and [hardware samples](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/guides/README.md#AnchorIDHardwareSamples) to learn how to connect various hardware platforms to ThingsBoard.

### Client-side libraries installation

Install preferred HTTP \(cURL\), MQTT \(Mosquitto or MQTT.js\) or CoAP \(CoAP.js\) client using following commands.

### Sample cURL command used in the video tutorial

This command works for Windows, Ubuntu and macOS, assuming that cURL tool is installed.

```bash
# Please replace $HOST_NAME and $ACCESS_TOKEN with corresponding values.
curl -v -X POST -d "{\"temperature\": 25}" $HOST_NAME/api/v1/$ACCESS_TOKEN/telemetry --header "Content-Type:application/json"

# For example, $HOST_NAME in case of live demo server:
curl -v -X POST -d "{\"temperature\": 25}" https://demo.thingsboard.io/api/v1/$ACCESS_TOKEN/telemetry --header "Content-Type:application/json"

# For example, $HOST_NAME in case of local installation:
curl -v -X POST -d "{\"temperature\": 25}" http://localhost:8080/api/v1/$ACCESS_TOKEN/telemetry --header "Content-Type:application/json"
```

### Sample generator script

```javascript
var msg = { temperature: +(Math.random()*5 + 25).toFixed(1)};
var metadata = {};
var msgType = "POST_TELEMETRY_REQUEST";

return { msg: msg, metadata: metadata, msgType: msgType };
```

### Rule Engine guides

[Rule Engine overview](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rule-engine-2-0/overview/README.md) - learn the Rule Engine basics and architecture.

[Rule Engine guides](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/guides/README.md#AnchorIDDataProcessing) - learn how to use ThingsBoard Rule Engine.

### Mail settings

Use this [guide](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/ui/mail-settings/README.md#step-31-sendgrid-configuration-example) to configure SendGrid or use any other SMTP server available.

### Other sample data files

**Create some folder** to store all necessary files for this tutorial. Download to this folder or create the following data files:

* * contains two device attributes values: firmware version and serial number.
* * contains three time-series values: temperature, humidity and active flag.

Please note that data in this files is basically in key-value format. You can use your own keys and values. See [MQTT](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/mqtt-api/README.md#key-value-format), [CoAP](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/coap-api/README.md#key-value-format) or [HTTP](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/http-api/README.md#key-value-format) protocol reference for more details.

### Pushing data using MQTT, CoAP or HTTP

Download the following files to **previously created folder** according to the preferred client:

* **MQTT.js \(MQTT\)**
  *  \(Ubuntu & MacOS\) or {% include ghlink.html content='mqtt-js.bat' ghlink='/docs/getting-started-guides/resources/mqtt-js.bat' %} \(Windows\)
  * 
* **Mosquitto \(MQTT\)**
  * 
* **CoAP.js \(CoAP\)**
  * 
* **cURL \(HTTP\)**
  * 

If you are using a shell script \(\*.sh\) make sure that it is executable:

```text
chmod +x *.sh
```

Before executing script don't forget to:

* replace **$ACCESS\_TOKEN** with one from **Device credentials** window.
* replace **$THINGSBOARD\_HOST** with either **127.0.0.1** \(in case of local installation\) or **demo.thingsboard.io** \(in case of live-demo\).

Finally, execute corresponding _.sh or_ .bat script to push data to the server.

Below are tabs with the content of the scripts provided.

## Next steps

## Your feedback

Don't hesitate to star ThingsBoard on [**github**](https://github.com/thingsboard/thingsboard) to help us spread the word. If you have some questions about this sample - post it on the [**forum**](https://groups.google.com/forum/#!forum/thingsboard).

