---
title: Getting Started with AEM and Adobe Target
seo-title: Getting Started with AEM and Adobe Target
description: An end-to-end tutorial showing how to create and deliver personalized experience using Adobe Experience Manager and Adobe Target. In this tutorial, you will also learn about different personas involved in the end to end process and how they collaborate with each other
seo-description: An end-to-end tutorial showing how to create and deliver personalized experience using Adobe Experience Manager and Adobe Target. In this tutorial, you will also learn about different personas involved in the end to end process and how they collaborate with each other
---

# Integrating Adobe Experience Manager with Adobe Target

In this section, we will be discussing how to set up Adobe Experience Manager with Adobe Target for different use cases. Based on your use case and organizational requirements, you can choose either one of the options, or both.

* **Method 1 - Using Launch, By Adobe via Adobe I/O Console**
    If your site is hosted on AEM, you can add Target libraries to your site pages using Adobe's Tag Management system, [Launch](https://docs.adobe.com/content/help/en/launch/using/overview.html) (*formerly known as DTM*). Launch provides a simple way to deploy and manage all tags necessary to power relevant customer experiences.
* **Method 2 - Using AEM legacy Cloud Services**
    For AEM customers, who would like to use Experience Fragment offers to create an activity within Adobe Target, you might need to integrate Adobe Target with AEM using the Legacy Cloud Services. This integration is required to push Experience Fragments from AEM to Target as HTML/JSON offers and to keep the target offers in sync with AEM. *This integration is required for implementing Use Case 1.*

## Using Launch, By Adobe via Adobe I/O Console

### Prerequisites

* AEM 6.5 (*recommend installing the Latest Service Pack*)
* Access to your organizations Adobe Experience Cloud - <https://>`<yourcompany>`.experiencecloud.adobe.com
* Experience Cloud provisioned with the following solutions
  * [Launch, By Adobe](https://marketing.adobe.com)
  * [Adobe Target](https://marketing.adobe.com)
  * [Adobe I/O Console](https://console.adobe.io)

>[!NOTE]
>
> Customer needs to be properly provisioned with Adobe Launch and Adobe I/O from [Adobe support](https://helpx.adobe.com/contact/enterprise-support.ec.html) or reach out to your system administrator

### Users Involved

For this integration, the following audiences needs to be involved, and to perform some tasks, you might need administrative acce ss.  

* Developer
* Experience Cloud Administrator

### Introduction

AEM offers an out of the box integration between AEM and Adobe Launch, which allows AEM administrators to easily configure AEM and Adobe Launch via an easy to use interface, which reduces the level of effort and the number of errors when configuring these two tools. And just by adding Adobe Target extension to Adobe launch will help us use all features of Adobe Target on the AEM web page(s).
