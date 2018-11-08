---
layout: docwithnav
assignees:
  - ikulikov
title: Building from sources
---

# building-from-source

This guide will help you to download and build ThingsBoard IoT Gateway from sources. Instructions listed below are tested on Ubuntu 16.04 and CentOS 7.1

## Required tools

This section contains installation instructions for build tools.

### Java

ThingsBoard IoT Gateway is build using Java 8. You can use [following instructions](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/iot-gateway/install/linux/README.md#step-1-install-java-8) to install Java 8.

### Maven

ThingsBoard IoT Gateway build requires Maven 3.1.0+.

**Please note** that maven installation may set Java 7 as a default JVM on certain Linux machines. Use java installation [instructions](building-from-source.md#java) to fix this.

## Source code

You can clone source code of the project from the official [github repo](https://github.com/thingsboard/thingsboard-gateway).

```bash
git clone git@github.com:thingsboard/thingsboard-gateway.git
# checkout latest release branch
git checkout release-1.0
```

## Build prerequisites

We assume you have already build ThingsBoard from sources using this [guide](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/install/building-from-source/README.md). The gateway project requires some maven dependencies that will be available after a local ThingsBoard build.

## Build

The following command will build gateway project:

```bash
mvn clean install
```

## Build artifacts

You can find debian, rpm and windows packages in the target folder:

```bash
thingsboard-gateway/target
```

