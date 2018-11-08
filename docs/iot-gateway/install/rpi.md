---
layout: docwithnav
assignees:
  - ikulikov
title: Installing ThingsBoard IoT Gateway on Raspberry Pi 3 Model B
description: Installing ThingsBoard IoT Gateway on Raspberry Pi 3 Model B
---

# rpi

* TOC

  {:toc}

This guide describes how to install ThingsBoard IoT Gateway on a Raspberry Pi 3 running Raspbian Jessie.

## Step 1. Install Java 8

IoT Gateway service is running on Java 8. Oracle Java 8 is already pre-installed on Raspbian. You can check java version using the following command

```bash
$ java -version
java version "1.8.0_65"
Java(TM) SE Runtime Environment (build 1.8.0_65-b17)
Java HotSpot(TM) Client VM (build 25.65-b01, mixed mode)
```

Any Java version higher than or equal to 1.8 is fine.

## Step 2. Download installation package

Download installation package or [build it from source](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/install/building-from-source/README.md).

```bash
# Download the package
$ wget https://github.com/thingsboard/thingsboard-gateway/releases/download/v1.4.0.1/tb-gateway-1.4.0.deb
```

## Step 3. Install gateway as a service

```bash
# Install gateway as a service
$ sudo dpkg -i tb-gateway-1.2.1.deb
# Update gateway memory usage and restrict it to 150MB in /etc/tb-gateway/conf/tb-gateway.conf
export JAVA_OPTS="$JAVA_OPTS -Dplatform=rpi -Xms150M -Xmx150M"
```

Congratulations! ThingsBoard IoT Gateway is now installed on your Raspberry as a service.

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

