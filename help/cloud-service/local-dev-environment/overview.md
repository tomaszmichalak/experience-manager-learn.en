---
title: Local Development Environment
description: Adobe Experience Manager (AEM) as a Cloud Service local development environment overview.
feature: 
topics: development
version: cloud-service
doc-type: article
activity: troubleshoot
audience: developer
kt:
---
 
# Local Development Environment

Adobe Experience Manager (AEM) as a Cloud Service local development environment overview.

![AEM as a Cloud Service Local Development Environment Technology Stack](./assets/overview/local-development-environment-overview.png)

The Local development environment for AEM as a Cloud Service can be broken up into three logical groups.

+ The __AEM Project__ contains the custom code, configuration and content that is the custom AEM application.
+ The __Local AEM Runtime__ which runs a local version of AEM Author and Publish services locally.
+ The __Local Dispatcher Runtime__ which runs a local version of Apache Web Server and Dispatcher.


## The Command line

AEM Project development requires a basic level of understanding of the OS's command line.

* macOS includes [Terminal](https://support.apple.com/guide/terminal/welcome/mac), or 3rd-party alternatives such as [iTerm2](https://iterm2.com/) can be used.
* Windows includes [PowerShell](https://docs.microsoft.com/en-us/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-6)
* Linux provides access to the Shell

## Install Homebrew

Homebrew is an open source package manager






## AEM Project

The AEM project is the custom code base containing the code, configuration and content that is deployed via Cloud Manager to AEM as a Cloud Service. The baseline project structure is generated via the [AEM Project Maven Archetype](https://github.com/adobe/aem-project-archetype).

+ Learn how to set up the local AEM Project

## Local AEM Runtime

The AEM as a Cloud Service SDK provides a QuickStart Jar that runs a local version for the AEM Cloud Service. The QuickStart Jar can be used to run either the AEM Author Service or AEM Publish Service locally. Note that while the QuickStart Jar provides a local development experience, not all features available in AEM as a Cloud Service are included in the QuickStart Jar.

As a new QuickStart Jar is released with every update of AEM as a Cloud Service, which happens daily, it is recommended developers also update the QuickStart Jar and their local QuickStart Jar installs frequently, at least bi-weekly.

+ Learn how to set up the Local AEM runtime

## Local Dispatcher Runtime

The AEM Dispatcher SDK provides everything required to set up the local Dispatcher runtime. The Dispatcher SDK is Docker based and provides command line tools to transpile baseline Apache Web Server and Dispatcher configuration files into a compatible formats and deploy them to Dispatcher running in the Docker container.

+ [Learn how to set up the Dispatcher SDK](../../../dispatcher/set-up-the-dispatcher-sdk.md)
