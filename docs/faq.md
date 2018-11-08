---
layout: docwithnav
title: FAQ
description: ThingsBoard FAQ
---

# faq

* TOC

  {:toc}

## What is ThingsBoard?

ThingsBoard is an open-source server-side platform that allows you to monitor and control your IoT devices. It is free for both personal and commercial usage and you can deploy it anywhere. If this is your first experience with the platform we recommend to review [what-is-thingsboard](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/getting-started-guides/what-is-thingsboard/README.md) and [getting started guide](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/getting-started-guides/helloworld/README.md). You can find more information on the dedicated page.

## How do I get started?

We recommend to [install](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/install/installation-options/README.md) ThingsBoard locally on your laptop or PC using Docker and follow the [getting started guide](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/getting-started-guides/helloworld/README.md).

## What can I do with ThingsBoard?

ThingsBoard provides out-of-the-box IoT solution that will enable server-side infrastructure for your IoT applications. You can find more information by browsing [guides](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/README.md) and [samples](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/samples/README.md)

## Where can I host ThingsBoard?

You can host ThingsBoard in the cloud, on-premises or locally on your laptop, PC or even Raspberry Pi. We recommend to get started with Docker installation

* [Linux & Mac OS](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/install/docker/README.md) 
* [Windows](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/install/docker-windows/README.md)

You can also take a look at [cluster setup](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/install/cluster-setup/README.md) guide.

## How to connect my device?

ThingsBoard provides [MQTT](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/mqtt-api/README.md), [CoAP](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/coap-api/README.md) and [HTTP](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/http-api/README.md) protocols support. **Existing** devices may be connected to the platform using [**ThingsBoard Gateway**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/what-is-iot-gateway/README.md). You can find more information on the [connectivity](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/protocols/README.md) page.

## Do I need to use an SDK?

No, many IoT devices can't afford to embed third-party SDK. ThingsBoard provides quite simple API over common IoT protocols. You can choose any client-side library you like or use your own. Some useful references:

* [MQTT client-side libraries list](https://github.com/mqtt/mqtt.github.io/wiki/libraries) 
* [C-implementation for CoAP](https://libcoap.net/)

## What about security?

You can use MQTT \(over SSL\) or HTTPS protocols for transport encryption.

Each device has unique access token credentials that is used to setup connection. Credentials type is pluggable, so X.509 certificates support is coming soon.

## How much devices can ThingsBoard support?

ThingsBoard platform is horizontally scalable. Each server node in the cluster is unique. Scalability is achieved using [consistent-hashing](https://dzone.com/articles/simple-magic-consistent) load balancing algorithm between the cluster nodes. Actual performance depends on usage scenario of connected devices. For example, small commodity hardware cluster can support [several millions](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/reference/performance/README.md) of devices connected over MQTT.

## Where does ThingsBoard store data?

The data is stored in [Cassandra](http://cassandra.apache.org/) database. Cassandra suites well for storage and querying of time-series data and provides high availability and fault-tolerance.

## What license type does ThingsBoard use?

ThingsBoard is licensed under [Apache 2.0 License](https://en.wikipedia.org/wiki/Apache_License#Version_2.0). It is free for both personal and commercial usage and you can deploy it anywhere.

## How to get support?

You can use troubleshooting instructions and community resources or [contact us](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/contact-us/README.md) and learn more about [services](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/services/README.md) we provide.

