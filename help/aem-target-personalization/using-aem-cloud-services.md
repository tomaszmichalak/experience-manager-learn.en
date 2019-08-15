---
title: Integrating AEM with Adobe Target using legacy cloud services
seo-title: Integrating AEM with Adobe Target using legacy cloud services
description: An end-to-end tutorial showing how to create and deliver personalized experience using Adobe Experience Manager and Adobe Target. In this tutorial, you will also learn about different personas involved in the end to end process and how they collaborate with each other
seo-description: An end-to-end tutorial showing how to create and deliver personalized experience using Adobe Experience Manager and Adobe Target. In this tutorial, you will also learn about different personas involved in the end to end process and how they collaborate with each other
---

# Using AEM legacy Cloud Services {#aem-target-cloud-services}

In this section, we will discuss how to set up Adobe Experience Manager with Adobe Target using legacy Cloud Services.

For AEM customers, who would like to use Experience Fragment offers to create an activity within Adobe Target, you might need to integrate Adobe Target with AEM using the Legacy Cloud Services. This integration is required to push Experience Fragments from AEM to Target as HTML/JSON offers and to keep the target offers in sync with AEM. *This integration is required for implementing Use Case 1.*

## Prerequisites

* **AEM**
    * AEM author and publish instance are necessary to complete this tutorial. If you haven't setup your AEM instance yet, you can follow the steps [here](./implementation.md#getting-aem).

* **Experience Cloud**
  * Access to your organizations Adobe Experience Cloud - <https://>`<yourcompany>`.experiencecloud.adobe.com
  * Experience Cloud provisioned with the following solutions
    * [Adobe Target](https://marketing.adobe.com)
  
    >[!NOTE]
    >
    > Customer needs to be properly provisioned with Adobe Launch and Adobe I/O from [Adobe support](https://helpx.adobe.com/contact/enterprise-support.ec.html) or reach out to your system administrator

### Integrating AEM with Adobe Target

#### General Steps

>[!VIDEO](https://video.tv.adobe.com/v/28428?quality=9)

1. Create Adobe Target Cloud Service using Adobe IMS Authentication (*Uses Adobe Target Standard API*) (00:34)
2. Obtain Adobe Target Client Code (01:50)
3. Create Adobe IMS Configuration for Adobe Target (02:08)
4. Create a Technical Account for accessing Target API within Adobe I/O Console (02:08)
5. Add Adobe Target Cloud Service to AEM Experience Fragments (04:12)

At this point, you have successfully integrated [AEM with Adobe Target using Legacy Cloud Services](./using-aem-cloud-services.md#integrating-aem-target-options) as detailed in Option 2. You should now be able to create an Experience Fragment within AEM, and publish the Experience Fragment as HTML offer or JSON Offer to Adobe Target, and can then be used to create an activity.

[NEXT CHAPTER](./using-launch-adobe-io.md): In the next chapter, you will be integrating Launch with AEM.
