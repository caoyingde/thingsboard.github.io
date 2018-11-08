---
layout: docwithnav
assignees:
  - ashvayka
title: Building from sources
description: Building ThingsBoard IoT platform from sources
---

# building-from-source

* TOC

  {:toc}

This guide will help you to download and build ThingsBoard from sources. Instructions listed below are tested on Ubuntu 16.04 and CentOS 7.1

## Required tools

This section contains installation instructions for build tools.

### Java

ThingsBoard is build using Java 8. You can use [following instructions](https://github.com/caoyingde/thingsboard.github.io/tree/9437083b88083a9b2563248432cbbe460867fbaf/docs/user-guide/install/linux/README.md#java) to install Java 8.

### Maven

ThingsBoard build requires Maven 3.1.0+.

**Please note** that maven installation may set Java 7 as a default JVM on certain Linux machines. Use java installation [instructions](building-from-source.md#java) to fix this.

## Source code

You can clone source code of the project from the official [github repo](https://github.com/thingsboard/thingsboard).

```bash
git clone git@github.com:thingsboard/thingsboard.git
# checkout latest release branch
git checkout release-2.0
```

## Build

Run the following command from the thingsboard folder to build the project:

```bash
mvn clean install
```

## Build artifacts

You can find debian, rpm and windows packages in the target folder:

```bash
application/target
```

