---
layout: docwithnav
assignees:
  - ikulikov
title: Installing ThingsBoard IoT Gateway on Linux
description: Installing ThingsBoard IoT Gateway on Linux
---

# linux

* TOC

  {:toc}

## Step 1. Install Java 8

IoT Gateway requires Java 8. Although you are able to start the service using [OpenJDK](http://openjdk.java.net/), the solution is actively tested on [Oracle JDK](http://www.oracle.com/technetwork/java/javase/overview/index.html).

Follow this instructions to install Oracle JDK 8:

* [Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04#installing-the-oracle-jdk)
* [CentOS 7](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8)

Please don't forget to configure your operating system to use Oracle JDK 8 by default. Corresponding instructions are in the same articles listed above.

## Step 2. Download installation package

Download installation package or [build it from source](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/install/building-from-source/README.md).

## Step 3. Install gateway as a service

Congratulations! ThingsBoard IoT Gateway is now installed on your Linux machine as a service.

## Step 4. Configure your gateway

Let's configure your gateway before we start it!

Let's skip extension configuration for now. We need to validate that gateway is able to successfully connect to ThingsBoard server first.

Navigate to the configuration folder **/etc/tb-gateway/conf** and configure connection to ThingsBoard server. See [**getting started**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/getting-started/README.md) or [**general configuration**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/configuration/README.md) for more details.

## Step 5. Launch your gateway

Now let's start the gateway! Execute the following command to start gateway:

```bash
sudo service tb-gateway start
```

In order to restart the gateway you can execute following commands

```bash
sudo service tb-gateway restart
```

## Step 6. Troubleshooting your installation

The log files are located in **/var/log/tb-gateway** folder.

The **tb-gateway.log** file should contain following line:

```text
YYYY-MM-DD HH:mm:ss,sss [main] INFO  o.t.gateway.GatewayApplication - Started GatewayApplication in x.xxx seconds (JVM running for x.xxx)
```

You can issue the following command in order to check if there are any errors on the backend side:

```bash
cat /var/log/tb-gateway/tb-gateway.log | grep ERROR
```

In case of any unclear errors, use general [troubleshooting guide](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/troubleshooting/README.md#getting-help) or [contact us](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/contact-us/README.md).

## Next Steps

Use [**OPC-UA**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/getting-started/README.md#step-9-connect-to-external-opc-ua-server), [**MQTT**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/getting-started/README.md#step-8-connect-to-external-mqtt-broker), [**Sigfox Backend**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/getting-started/README.md#step-10-connect-to-sigfox-backend) or [**Modbus slave**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/getting-started/README.md#step-11-connect-to-modbus-slave) extensions to integrate your devices with ThingsBoard platform.

