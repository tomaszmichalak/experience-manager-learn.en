---
title: Local Development Environment
description: Adobe Experience Manager (AEM) local development environment overview.
feature: 
topics: development
version: cloud-service
doc-type: article
activity: troubleshoot
audience: developer
kt: 3290
---
 
# Local Development Environment Set up

This tutorial walks through setting up a local development environment for Adobe Experience Manager (AEM) using the AEM as a Cloud Service SDK. Included are the development tooling required to develop, build and compile AEM Projects, as well as local runtimes allowing developers to quickly validate new features locally before deploying them to AEM as a Cloud Service via Adobe Cloud Manager.

![AEM as a Cloud Service Local Development Environment Technology Stack](./assets/overview/aem-sdk-technology-stack.png)

The local development environment for AEM can be broken up into three logical groups:

+ The __AEM Project__ contains the custom code, configuration and content that is the custom AEM application.
+ The __Local AEM Runtime__ which runs a local version of AEM Author and Publish services locally.
+ The __Local Dispatcher Runtime__ which runs a local version of Apache HTTP Web Server and Dispatcher.

## Development Tools for AEM Projects

The AEM project is the custom code base containing the code, configuration and content that is deployed via Cloud Manager to AEM as a Cloud Service. The baseline project structure is generated via the [AEM Project Maven Archetype](https://github.com/adobe/aem-project-archetype).

+ [Set up Development Tools for AEM Projects](./development-tools.md)

## Local AEM Runtime

The AEM as a Cloud Service SDK provides a QuickStart Jar that runs a local version of AEM. The Quickstart Jar can be used to run either the AEM Author Service or AEM Publish Service locally. Note that while the Quickstart Jar provides a local development experience, not all features available in AEM as a Cloud Service are included in the Quickstart Jar.

+ [Set up the Local AEM runtime](./aem-runtime.md)

## Local Dispatcher Runtime

The Dispatcher Tools provides everything required to set up the local Dispatcher runtime. Dispatcher Tools are Docker-based and provides command line tools to transpile Apache HTTP Web Server and Dispatcher configuration files into a compatible formats and deploy them to Dispatcher running in the Docker container.

+ [Set up the Local Dispatcher Runtime](./dispatcher-tools.md)
