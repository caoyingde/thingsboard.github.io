---
layout: docwithnav
title: Aggregate latest telemetry values periodically
description: Calculate average temperature in the warehouse
---

# aggregate-latest-data

This tutorial will show how to calculate average temperature in the warehouse based on readings from multiple temperature sensors inside the warehouse.

* TOC

  {:toc}

## Use case

Let's assume you have a warehouse with multiple temperature sensors. For example, one per each zone. Let's also assume temperature readings are reported by the sensor only when it detects temperature change. Thus, some sensors may have been inactive for a week although some sensors may report temperature change just recently.

In this tutorial we will configure ThingsBoard Rule Engine to automatically calculate average temperature in the warehouse based on latest readings from multiple temperature sensors every minute. Please note that this is just a simple theoretical use case to demonstrate the capabilities of the platform. You can use this tutorial as a basis for much more complex scenarios.

We will use 1 warehouse, 2 sensors and 1 minute execution period just for demo purposes.

## Prerequisites

We assume you have completed the following guides and reviewed the articles listed below:

* [Getting Started](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/getting-started-guides/helloworld/README.md) guide.
* [Rule Engine Overview](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rule-engine-2-0/overview/README.md).

## Model definition

We will create one asset that has name "Warehouse A" and type "warehouse". We will add this asset to an asset group called "Warehouses".

![image](../../../../.gitbook/assets/add-asset.png)

We will create two devices that has names "Sensor A1" and "Sensor A2" and type "thermometer". We will add this devices to device group called "Thermometers".

![image](../../../../.gitbook/assets/add-meters%20%281%29.png)

We must also create relations between the warehouse asset and thermometers. This relation will be used in the rule chain to associate thermometer readings with the warehouse itself. It is also convenient to use relations in the dashboards to provide drill-down capabilities. You may notice two outbound relations from the warehouse asset to the thermometers on the screenshot below:

![image](../../../../.gitbook/assets/add-relations.png)

**Note**: Please review the following [**documentation page**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/entities-and-relations/README.md) to learn how to create assets and relations.

## Message Flow

In this section, we explain the purpose of each node in this tutorial. There will be two rule chains involved:

* "Thermometer Emulators" - optional rule chain to simulate data from two temperature sensors; 
* "Warehouse Temperature" - rule chain that actually calculates average temperature in the warehouse;

### Thermometer Emulators rule chain

![image](../../../../.gitbook/assets/emulator-rule-chain.png)

* **Nodes A and B**: Generator nodes

  * Two similar nodes that periodically generate a very simple message with random temperature reading.

  ![image](../../../../.gitbook/assets/nodes-a-and-b%20%281%29.png)

* **Node C**: Rule Chain node
  * Forwards all messages to default rule chain.

### Warehouse Temperature rule chain

![image](../../../../.gitbook/assets/aggregation-rule-chain%20%281%29.png)

* **Node D**: Aggregate latest. Periodically \(period of execution is defined as "Execution period value"\) executes the following:

  * Fetches all devices related to the "Warehouse A" asset using "Contains" relation.
  * Fetches latest temperature reading for each of the devices and calculates average temperature reading.
  * Generates "POST\_TELEMETRY\_REQUEST" message that contains value of the average temperature.

  ![image](../../../../.gitbook/assets/node-d-part1.png)

  ![image](../../../../.gitbook/assets/node-d-part2.png)

* **Node E**: Save telemetry node
  * Simple node that stores incoming message to the database and dispatches updates to the subscribers.

## Configuring the Rule Chains

Download and [**import**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/ui/rule-chains/README.md#rule-chains-importexport) attached emulators rule chain [**file**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rule-engine-2-0/pe/tutorials/thermometer_emulators.json) as a new "Thermometer Emulators" rule chain and attached warehouse temperature rule chain [**file**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rule-engine-2-0/pe/tutorials/warehouse_temperature.json) as a new "Warehouse Temperature" rule chain. Please note that some nodes have debug enabled. This affects performance. Create Node C as shown on the image above in the thermometer emulators rule chain to forward telemetry to the root rule chain.

## Validating the flow

Download and [**import**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/ui/dashboards/README.md#iot-dashboard-importexport) attached dashboard [**file**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/rule-engine-2-0/pe/tutorials/warehouse_thermometers.json) as a new "Warehouse Temperature" dashboard.

![image](../../../../.gitbook/assets/dashboard-part1%20%281%29.png)

Note that you can drill down to the chart for particular warehouse by clicking on the corresponding row.

![image](../../../../.gitbook/assets/dashboard-part2%20%281%29.png)

## Next steps

