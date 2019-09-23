---
title: Getting Started with AEM and Adobe Target
seo-title: Getting Started with AEM and Adobe Target
description: An end-to-end tutorial showing how to create and deliver personalized experience using Adobe Experience Manager and Adobe Target. In this tutorial, you will also learn about different personas involved in the end to end process and how they collaborate with each other
seo-description: An end-to-end tutorial showing how to create and deliver personalized experience using Adobe Experience Manager and Adobe Target. In this tutorial, you will also learn about different personas involved in the end to end process and how they collaborate with each other
---

# Using Adobe Experience Platform Launch via Adobe I/O Console

## Prerequisites

* [AEM author and publish instance](./implementation.md#getting-aem) running on localhost 4502 and 4503 respectively
* **Experience Cloud**
  * Access to your organizations Adobe Experience Cloud - <https://>`<yourcompany>`.experiencecloud.adobe.com
  * Experience Cloud provisioned with the following solutions
    * [Adobe Experience Platform Launch](https://marketing.adobe.com)
    * [Adobe Target](https://marketing.adobe.com)
    * [Adobe I/O Console](https://console.adobe.io)
  
    > [!NOTE]
    >You should have permission to Develop, Approve, Publish, Manage Extensions, and Manage Environments in Launch. If you are unable to complete any of these steps because the user interface options are not available to you, reach out to your Experience Cloud Administrator to request access. For more information on Launch permissions, [see the documentation](https://docs.adobelaunch.com/administration/user-permissions).

* **Browser Plugins**
  * Adobe Experience Cloud Debugger ([Chrome](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj))
  * Launch and DTM Switch ([Chrome](https://chrome.google.com/webstore/detail/launch-and-dtm-switch/nlgdemkdapolikbjimjajpmonpbpmipk))

## Users Involved

For this integration, the following audiences need to be involved, and to perform some tasks, you might need administrative access.

* Developer
* AEM Admin
* Experience Cloud Administrator

## Introduction

AEM offers an out of the box integration with Adobe Launch. This integration allows AEM administrators to easily configure Adobe Launch via an easy to use interface, thereby reducing the level of effort and number of errors, when configuring these two tools. And just by adding Adobe Target extension to Adobe launch will help us use all features of Adobe Target on the AEM web page(s).

In this section, we would be cover the following integration steps:

* Launch
  * Create a Launch Property
  * Adding Target Extension
  * Create a Data Element
  * Create a Page Rule
  * Setup Environments
  * Build and Publish
* AEM
  * Create a Cloud Service
  * Create

### Launch

#### Create a Launch Property

A property is a container that you fill with extensions, rules, data elements, and libraries as you deploy tags to your site.

1. Navigate to your organizations [Adobe Experience Cloud](https://experiencecloud.adobe.com/) (<https://>`<yourcompany>`.experiencecloud.adobe.com)
2. Log in using your Adobe ID, and make sure you are in the right organization.
3. From the solution switcher, click on **Launch** and then select the **Go To Launch** button.

    ![Experience Cloud - Launch](assets/using-launch-adobe-io/exc-cloud-launch.png)

    >[!VIDEO](https://video.tv.adobe.com/v/28379t1?quality=9)

    You should now see the Properties screen (if no properties have ever been created in the account, this screen might be empty). Let's create a new property for our tutorial.

    A property can be any grouping of one or more domains and subdomains. You can manage and track these assets similarly. For example, suppose that you have multiple websites based on one template, and you want to track the same assets on all of them. You can apply one property to multiple domains. For more information on creating properties, see ["Create a Property"](https://docs.adobelaunch.com/administration/companies-and-properties#create-a-property) in the product documentation.

4. Click on the **New Property** button
5. Provide a name for your property ( For example, *AEM Target Tutorial*)
6. As the domain, enter "*localhost.com*" since this is the domain where the WKND demo site is running on. Although the "Domain" field is required, the Launch property will work on any domain where it's implemented. Primary purpose of this field is to pre-populate menu options in the Rule builder.
7. Click the **Save** button.

    ![Launch -New Property](assets/using-launch-adobe-io/exc-launch-property.png)

8. Open the property that you just created and click on the Extensions tab.

#### Adding Target Extension

The Adobe Target extension supports client-side implementations using Target's JavaScript SDK for the modern web, at.js. Customers still using Target's older library, mbox.js, [should upgrade to at.js](https://marketing.adobe.com/resources/help/en_US/target/ov2/t_target-migrate-atjs.html) to use Launch.

The Target extension consists of two main parts:

* The extension configuration, which manages the core library settings
* Rule actions to do the following:
  * Load Target (at.js)
  * Add Params to All Mboxes
  * Add Params to Global Mbox
  * Fire Global Mbox

1. Under **Extensions**, you can see the list of Extensions that are already installed for your Launch property. ([Adobe Launch Core Extension](https://exchange.adobe.com/experiencecloud.details.100223.adobe-launch-core-extension.html) is installed by default)
2. Click on the **Extension Catalog** option, and search for Target in the filter.
3. Select the latest version of Adobe Target's at.js and Click on **Install** option.
    ![Launch -New Property](assets/using-launch-adobe-io/launch-target-extension.png)

4. Click on **Configure** button, and you can notice the configuration window with your Target account credentials imported, and the at.js version for this extension.
     ![Target - Extension Config](assets/using-launch-adobe-io/launch-target-extension-2.png)

    When Target is deployed via asynchronous Launch embed codes, you should hardcode a pre-hiding snippet on your pages before the Launch embed codes in order to manage content flicker. We will learn more about the pre-hiding snipper later. You can download the pre-hiding snippet [here](assets/using-launch-adobe-io/prehiding.js)

5. Click **Save** to complete adding the Target extension to your Launch property, and you should now be able to see the Target extension listed under the **Installed** extensions list.

6. Repeat the steps above to search for "Experience Cloud ID Service" extension and install it.
   ![Extension - Experience Cloud ID Service](assets/using-launch-adobe-io/launch-extension-experience-cloud.png)

#### Create a Data Element {#launch-data-element}

[Data Element Documentation](https://docs.adobe.com/content/help/en/launch/using/reference/manage-resources/data-elements.html)

1. Click on the **Data Elements** tab for your site property, and let's create a new data element to collect your page information.

    ![Launch - Data Element](assets/using-launch-adobe-io/launch-create-data-element.png)

2. Create a ***PageName*** data element with the following javascript path variable : *digitalData.page.pageInfo.pageName* and save your changes.

    ![Data Element - Page Name](assets/using-launch-adobe-io/launch-de-pagename.png)

    > [!NOTE]
    > Digital data layer script added in the implementations' section of this tutorial can be accessed using the *digitalData* JS object to collect page information.

#### Create a Page Rule

[Rules Documentation](https://adobe.com/go/launch_help_rules_en)
1. Click on the **Rules** tab for your site property, and let's create a new rule.
    ![Rule - Page Load](assets/using-launch-adobe-io/launch-create-rule.png)
2. Provide a rule name, select the event type, create an action for your rule, and Save your changes.
    >[!VIDEO](https://video.tv.adobe.com/v/28411t1?quality=9)
    * [Events](https://docs.adobe.com/content/help/en/launch/using/reference/manage-resources/rules.html)
      * Extension - *Core*
      * Event Type - *Library Loaded (Page Top)*
      * Order - *50*
    * [Actions](https://docs.adobe.com/content/help/en/launch/using/reference/manage-resources/rules.html)
      * Action 1: To print page name in the console
        * Extension - Core
        * Action Type - Custom Code
        * Language - Javascript
        * In the JS Editor, provide the script as :
        ```console.log('Your Page name is'+_satellite.getVar('PageName'));```
      * Action 2: Add Target Libraries to your site pages
        * Extension - Adobe Target v2
        * Action Type - Load Target
      * Action 3: Sending page name as a Parameter to Page Load Request
        * Extension - Adobe Target v2
        * Action Type - Add Params to Page Load Request
      * Action 4: Fire Page Load Request
        * Extension - Adobe Target v2
        * Action Type - Fire Page Load Request

    >[!VIDEO](https://video.tv.adobe.com/v/28423?quality=9)

#### Setup Environments

1. Click on the **Environment** tab for your site property, and you can see the list of environment that gets created for your site property. By default, we have one instance each created for development, staging, and production.

 ![Data Element - Page Name](assets/using-launch-adobe-io/launch-environment-setup.png)

#### Build and Publish

1. Click on the **Publishing** tab for your site property, and let's create a library to build, and deploy our changes (data elements, rules) to a development environment.
    >[!VIDEO](https://video.tv.adobe.com/v/28412t1?quality=9)
2. Publish your changes from the Development to a Staging environment.
    >[!VIDEO](https://video.tv.adobe.com/v/28419t1?quality=9)
3. Run the **Build for Staging option**. 
4. Once the build is complete, run **Approve for Publishing**, which moves your changes from a Staging environment to a Production environment.
  ![Staging to Production](assets/using-launch-adobe-io/build-staging.png)
5. Finally, run the **Build and Publish to production** option to push your changes to production.
  ![Build and Publish to Production](assets/using-launch-adobe-io/build-and-publish.png)
  
### Adobe Experience Manager

1. From your [AEM author home page](http://localhost:4502/aem/start.html), click on Tools, Security, and select Adobe IMS Configuration.

#### General Steps

>[!VIDEO](https://video.tv.adobe.com/v/28416?quality=9)

1. Create IMS integration in AEM using credentials from Adobe I/O. (01:12 to 03:55)
2. In Adobe Launch, create a property. (covered [above](#create-launch-property))
3. Using the IMS integration from Step 1, create Adobe Launch integration to import your Launch property.
4. In AEM, map the Adobe Launch integration to a site using browser configuration. (05:28 to 06:14)
5. Validate integration manually. (06:15 to 06:33)
6. Using Launch/DTM browser plugin. (06:34 to 06:50)
7. Using Adobe Experience Cloud Debugger browser plugin. (06:51 to 07:22)

At this point, you have successfully integrated [AEM with Adobe Target using Adobe Experience Platform Launch](./using-aem-cloud-services.md#integrating-aem-target-options) as detailed in Option 1.

For using AEM Experience Fragment offers to power you personalization activities, lets proceed to the next chapter, and integrate AEM with Adobe Target using the legacy cloud services.

[NEXT CHAPTER](./using-aem-cloud-services.md): In the next chapter, you will be integrating Launch with AEM using Legacy Cloud Services.
