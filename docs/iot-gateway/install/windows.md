---
layout: docwithnav
assignees:
  - ashvayka
title: Installing ThingsBoard IoT Gateway on Windows
description: Installing ThingsBoard IoT Gateway on Windows
---

# windows

* TOC

  {:toc}

## Step 1. Install Java 8

IoT Gateway requires Java 8. If you don't have Java installed, please download and install Java 8 using this [link](https://java.com/en/download/).

## Step 2. Download and unzip installation files

Create a working directory, for example, "C:\tb-gateway". Download and unzip [this installation archive](https://github.com/thingsboard/thingsboard-gateway/releases/download/v1.4.0.1/tb-gateway-windows-1.4.0.zip) to the working directory. The working directory should look like this after installation

![image](../../../.gitbook/assets/windows-folder%20%281%29.png)

## Step 3. Run installation script

Run **install.bat** script to install Gateway as a Windows service. This means it will be automatically started on system startup. Similar, **uninstall.bat** will remove Gateway from Windows services.

**NOTE** Scripts listed above should be executed using Administrator Role.

```text
C:\tb-gateway>install.bat
Detecting if it is 64-bit machine
CurrentVersion 1.8
Java 1.8 found!
Installing tb-gateway ...
2017-01-31 02:26:50,704 INFO  - Starting ServiceWrapper in the CLI mode
2017-01-31 02:26:50,907 INFO  - Completed. Exit code is 0
DONE.
```

Congratulations! ThingsBoard IoT Gateway is now installed on your Windows machine as a service.

## Step 4. Configure your gateway

Let's configure your gateway before we start it!

Let's skip extension configuration for now. We need to validate that gateway is able to successfully connect to ThingsBoard server first.

Navigate to the configuration folder \("C:\tb-gateway\conf" in our case\) and configure the connection to ThingsBoard server. See [**getting started**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/getting-started/README.md) or [**general configuration**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/configuration/README.md) for more details.

## Step 5. Launch your gateway

Now let's start the gateway! Open command prompt as an Administrator and execute the following command

```text
net start tb-gateway
```

Expected output:

```text
The ThingsBoard Gateway service is starting.
The ThingsBoard Gateway service was started successfully.
```

In order to restart the gateway you can execute following commands

```text
net stop tb-gateway
net start tb-gateway
```

## Step 6. Troubleshooting your installation

The log files are located in **logs** folder \("C:\tb-gateway\logs" in our case\).

The **tb-gateway.log** file should contain following line:

```text
YYYY-MM-DD HH:mm:ss,sss [main] INFO  o.t.gateway.GatewayApplication - Started GatewayApplication in x.xxx seconds (JVM running for x.xxx)
```

In case of any unclear errors, use general [troubleshooting guide](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/troubleshooting/README.md#getting-help) or [contact us](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/contact-us/README.md).

## Next Steps

Use [**OPC-UA**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/getting-started/README.md#step-9-connect-to-external-opc-ua-server), [**MQTT**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/getting-started/README.md#step-8-connect-to-external-mqtt-broker), [**Sigfox Backend**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/getting-started/README.md#step-10-connect-to-sigfox-backend) or [**Modbus slave**](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/getting-started/README.md#step-11-connect-to-modbus-slave) extensions to integrate your devices with ThingsBoard platform.

