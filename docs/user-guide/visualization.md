---
layout: docwithnav
assignees:
  - ashvayka
title: Data Visualization
description: >-
  IoT data visualization for various IoT projects using iot dashboards,
  dashboard widgets and real-time charts
---

# visualization

* TOC

  {:toc}

ThingsBoard allows you to configure customizable IoT dashboards. Each IoT Dashboard may contain multiple dashboard widgets that visualize data from multiple IoT devices. Once IoT Dashboard is created, you may assign it to one of the customers of you IoT project.

IoT Dashboards are light-weight and you may have millions of dashboards. For example, you may automatically create a dashboard for each new customer based on data from registered customer IoT devices. Or you may modify dashboard via script when a new device is assigned to a customer. All these actions may be done manually or automated via REST API.

You can find useful links to get started below:

* [Getting started guide](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/getting-started-guides/helloworld/README.md) - will cover basic steps to create a dashboard.
* [IoT Dashboards](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/ui/dashboards/README.md) - contains tutorials about basic IoT dashboard operations.
* [Samples](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/samples/README.md) - contains several examples that include both client-side applications and corresponding data visualization.
* [Widget Library](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/ui/widget-library/README.md) - contains an overview of dashboard widget bundles:
  * **Digital** and **analog** gauges for latest real-time values visualization 
  * Highly customizable Bar and Line **charts** for visualization of historical and sliding-window data points  
  * **Map widgets** for tracking movement and latest positions of IoT devices on Google or OpenStreet maps.
  * **GPIO** control widgets that allow sending GPIO toggle commands to devices.
  * **Card** widgets to enhance your dashboards with flexible HTML labels based on static content or latest telemetry values from IoT devices. 

