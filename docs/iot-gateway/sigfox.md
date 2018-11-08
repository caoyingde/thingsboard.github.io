---
layout: docwithnav
assignees:
  - ashvayka
title: Sigfox IoT Extension Configuration
description: Sigfox support for ThingsBoard IoT Gateway
---

# sigfox

* TOC

  {:toc}

This guide will help you to get familiar with Sigfox extension configuration for ThingsBoard IoT Gateway. Use [general configuration](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/configuration/README.md) to enable this extension. We will describe extension configuration file below.

### Extension configuration: sigfox-config.json

Extension configuration is a JSON file that contains information about how to map incoming HTTP request based on Sigfox Device Type Id. The root JSON element should contain "deviceTypeConfigurations" array. Each configuration consists of device type id, security token, and converter:

#### Basic connection properties

| **Property** | **Description** | **Default Value** |
| :--- | :--- | :--- |
| deviceTypeId | Your Sigfox device type id | none |
| token | Your security token that needs to be present in "Authorization" header | none |
| converter | Describes how to convert incoming JSON to attribute and telemetry updates | none |

For Example:

```javascript
{
  "deviceTypeConfigurations": [
    {
      "deviceTypeId": "YOUR_DEVICE_TYPE_ID",
      "token": "SECURITY_TOKEN",
      "converter": {
        ...
      }
    }
  ]
}
```

#### Sigfox converter

This section will describe various configuration options that allow specifying the mapping between ThingsBoard features and Sigfox device data.

**Attributes & Timeseries data upload**

The "**converter**" configuration setup rules of MQTT topics monitoring and data conversion to ThingsBoard Key-Value format. For example:

```javascript
{
...
      "converter": {
        "deviceNameJsonExpression": "${$.device}",
        "attributes": [
          {
            "type": "string",
            "key": "lat",
            "value": "${$.lat}"
          },
          {
            "type": "string",
            "key": "lng",
            "value": "${$.lng}"
          }
        ],
        "timeseries": [
          {
            "type": "double",
            "key": "temperature",
            "value": "${$.data.temperature}",
            "transformer": {
              "type": "intToDouble"
            }
          },
          {
            "type": "double",
            "key": "humidity",
            "value": "${$.data.humidity}",
            "transformer": {
              "type": "intToDouble"
            }
          }
        ]
      }
...      
}
```

Each message that is published to this topic by other devices or applications is analyzed to extract device name and device data \(attributes or timeseries values\). The Json converter is based on [**JsonPath**](https://github.com/jayway/JsonPath) library to provide the ability of flexible mapping and filtering of JSON structures. You can define **filterExpression** based on the [**path**](https://github.com/jayway/JsonPath#path-examples) examples.

The **deviceNameJsonExpression** mapping parameter is used to extract device name from the incoming JSON message.

For example, if you have following message:

```javascript
{"serialNumber":"SN-001", "model":"T1000", "temperature":36.6}
```

The **"${$.serialNumber}"** expression will return **"SN-001"** device name. Similar, **"Device ${$.serialNumber} \(${$.model}\)"** will return **"Device SN-001 \(T1000\)"** device name.

Similar [**JsonPath**](https://github.com/jayway/JsonPath) mapping rules are applied for **attributes** and **timeseries** values:

* **key** - constant Attribute or Timeseries ThingsBoard key.
* **type** - either boolean, long, double or string.
* **value** - expression based on JsonPath syntax that may be specified inside **${}**

As a gateway developer, you are able to fork and add custom transformers using following [interface](https://github.com/thingsboard/thingsboard-gateway/blob/release-1.2/src/main/java/org/thingsboard/gateway/extensions/sigfox/conf/mapping/DataValueTransformer.java). Feel free to submit PRs with your custom transformer implementations if you believe that they may be useful for the ThingsBoard community.

## Next steps

Explore examples:

* [Sigfox Beckend connection example](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/getting-started/README.md#step-10-connect-to-sigfox-backend)

Explore guides related to main ThingsBoard features:

* [Data Visualization](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/visualization/README.md) - how to visualize collected data.
* [Device attributes](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/attributes/README.md) - how to use device attributes.
* [Telemetry data collection](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/telemetry/README.md) - how to collect telemetry data.
* [Using RPC capabilities](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rpc/README.md) - how to send commands to/from devices.
* [Rule Engine](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rule-engine/README.md) - how to use rule engine to analyze data from devices.

