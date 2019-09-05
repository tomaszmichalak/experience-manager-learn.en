---
title: Getting Started with AEM and Adobe Target
seo-title: Getting Started with AEM and Adobe Target
description: An end-to-end tutorial showing how to create and deliver personalized experience using Adobe Experience Manager and Adobe Target. In this tutorial, you will also learn about different personas involved in the end to end process and how they collaborate with each other
seo-description: An end-to-end tutorial showing how to create and deliver personalized experience using Adobe Experience Manager and Adobe Target. In this tutorial, you will also learn about different personas involved in the end to end process and how they collaborate with each other
---

# Personalization using AEM Experience Fragments and Adobe Target

Using experience fragments created in AEM in Target activities lets you combine the ease-of-use and power of AEM with powerful Automated Intelligence (AI) and Machine Learning (ML) capabilities in Target to test and personalize experiences at scale.

AEM brings together all of your content and assets in a central location to fuel your personalization strategy. AEM lets you easily create content for desktops, tablets, and mobile devices in one location without writing code. There’s no need to create pages for every device—AEM automatically adjusts each experience using your content.

Target lets you deliver personalized experiences at scale based on a combination of rules-based and AI-driven machine learning approaches that incorporate behavioral, contextual, and offline variables.  With Target, you can easily set up and run A/B and Multivariate (MVT) activities to determine the best offers, content, and experiences.

Experience fragments represent a huge step forward to link the content/experience creators and managers to the optimization and personalization professionals who are driving business outcomes using Target.

## Prerequisites

* **AEM**
  * [AEM author and publish instance](./implementation.md#getting-aem) running on localhost 4502 and 4503 respectively. Before your proceed with the tutorial, make sure 
* **Experience Cloud**
  * Access to your organizations Adobe Experience Cloud - <https://>`<yourcompany>`.experiencecloud.adobe.com
  * Experience Cloud provisioned with the following solutions
    * [Adobe Target](https://marketing.adobe.com)

## WKND Site - Use Case {#wknd-site-use-case}

WKND site is planning to announce a "SkateFest Challenge" across America through their website, and would like to have their site users sign up for the audition, to be conducted in each state. As a marketer, you have been assigned the task to run a campaign on the WKND site home page, with banners showing the nearest venue for audition and a link to event details page based on users current location. Let us explore the WKND site home page and learn how to create and deliver personalized experience for a user based off his/her current location.

## Users Involved

For this exercise, the following users needs to be involved, and to perform some tasks, you might need administrative access.

* Content Producer / Content Editor (Adobe Experience Manager)
* Marketer (Adobe Target / Optimization Team)

## WKND Site Home Page

 ![AEM Target Use Case 1](assets/personalization-use-case-1/aem-target-use-case-1-4.png)

1. Marketer initiates the WKND SkateFest campaign discussion with AEM Content Editor and details the requirements.
   * ***Requirement*** :Promote WKND SkateFest campaign on WKND site home page with personalized content for visitors from each state in the United States. Add a new content block beneath the Home Page Carousel containing a background image, text, and a button.
     * **Background Image** : Image should be relevant to the state from which the user is visiting the WKND Site page.
     * **Text** : "Sign Up for the Auditions"
     * **Button** : "Event Details" pointing to the WKND SkateFest Page
     * **WKND SkateFest Page** : a new page with event details including the audition venue, date, and time.
2. Based on the requirements, AEM Content Editor then creates an Experience Fragment for the content block and then later exports it to Adobe Target as an offer. To serve personalized content for all states in the United States, content author can create one Experience Fragment master variation and then create 50 other variations based off the master variation, one for each state. Content for each variation with relevant images and text can then be edited manually. When authoring an Experience Fragment, content editors can quickly access all the assets available within AEM Assets using the Asset Finder option. When an Experience Fragment gets exported to Adobe Target, all its variations are also pushed to Adobe Target as offers.

3. After exporting Experience Fragment from AEM to Adobe Target as Offers, marketers can then create an activity using these offers. Based off the WKND site SkateFest campaign, marketer needs to create and deliver personalized experience to WKND site visitors from each state in the United States of America. For a marketer, to create an Experience Targeting activity, you need to identify the audiences. For our WKND SkateFest campaign, we need to create 50 separate audiences, based on their location from which they are visiting the WKND website.
   * [Audiences](https://docs.adobe.com/content/help/en/target/using/introduction/target-key-concepts.html#section_3F32DA46BDF947878DD79DBB97040D01) define the target for your activity and are used anywhere where targeting is available. Target audiences are a defined set of visitor criteria. Offers can be targeted to specific audiences (or segments). Only visitors who belong to that audience see the experience that is targeted to them. For example, you might target an activity to an audience made up of visitors who use a particular browser or from a specific geo location.
   * An [offer](https://docs.adobe.com/content/help/en/target/using/introduction/target-key-concepts.html#section_973D4CC4CEB44711BBB9A21BF74B89E9) is the content displayed on your webpages during campaigns or activities. When you test your webpages, you measure the success of each experience with different offers in your locations. An offer can contain different types of content, including:
     * Image
     * Text
     * **HTML** *(We will be using the HTML Offers for our Activity)*
     * Link
     * Button

## Content Editor {#content-editor}

>[!VIDEO](https://video.tv.adobe.com/v/28596?quality=9)
> [!NOTE]
> Publish the Experience Fragment before exporting it to Adobe Target.

## Marketer {#marketer}

### Create an Audience with Geo Targeting {#marketer-audience}

1. Navigate to your organizations [Adobe Experience Cloud](https://experiencecloud.adobe.com/) (<https://>`<yourcompany>`.experiencecloud.adobe.com)
2. Login using your Adobe ID, and make sure you are in the right organization.
3. From the solution switcher, click on **Target** and then **Launch** Adobe Target.

    ![Experience Cloud- Adobe Target](assets/personalization-use-case-1/exp-cloud-adobe-target.png)

4. Navigate to the **Offers** tab and search for "WKND" offers. You should be able to see the list of experience fragments variations, exported from AEM as HTML Offers. Each offer corresponds to a state. For example, *WKND SkateFest California*, is the offer that gets served to a WKND Site visitor from California.

    ![Experience Cloud- Adobe Target](assets/personalization-use-case-1/html-offers.png)

5. From the main navigation, click on **Audiences**.

   Marketer needs to create 50 separate audiences for WKND site visitors coming from each state in the United States of America.

6. To create an audience, click on **Create Audience** button, and provide a name for your audience.

    **Audience Name format : WKND-\<*state*\>**

    ![Experience Cloud- Adobe Target](assets/personalization-use-case-1/audience-target-1.png)

7. Click **Add Rule > Geo**
8. Click **Select**, then select one of the following options:
    * Country
    * **State** *(Select State for WKND Site SkateFest Campaign)*
    * City
    * Zip Code
    * Latitude
    * Longitude
    * DMA
    * Mobile Carrier

    **Geo** - Use audiences to target users based on their geographical location, including their country, state/province, city, zip/postal code, DMA, or mobile carrier. Geo location parameters allow you to target activities and experiences based on your visitors' geography. You can include or exclude visitors based on their country, state/province, city, zip/postal code, latitude, longitude, DMA, or mobile carrier. This data is sent with each Target request and is based on the visitor's IP address. Select these parameters just like any targeting values.

    > [!NOTE]
    > A visitor's IP address is passed with a mbox request, once per visit (session), to resolve geo targeting parameters for that visitor.

9. Select the operator as **matches**, provide an appropriate value (For eg: California) and **Save** your changes. In our case, provide the state name.

    ![Adobe Target- Geo Rule](assets/personalization-use-case-1/audience-geo-rule.png)

    > [!NOTE]
    > You can have multiple rules assigned to an audience.

10. Repeat steps 6-9 to create audiences for the other states.

    ![Adobe Target- WKND Audiences](assets/personalization-use-case-1/adobe-target-audiences-50.png)

At this point, we have successfully created audiences for all WKND Site visitors across different states in the United States of America and also have the corresponding HTML offer for each state. So now let's create an Experience Targeting activity to target the audience with a corresponding offer for the WKND Site Home Page.

### Create an Activity with Geo Targeting {#marketer-activity}

1. From you Adobe Target window, navigate to **Activites** tab.
2. Click **Create Activity** and select the **Experience Targeting** activity type.
3. Select the **Web** channel and choose Eperience Composer as **Visual**.
4. Enter the **Activity URL** and Click **Next** to open the Virtual Experience Composer.

    WKND Site Home Page Publish URL: http://localhost:4503/content/wknd/en.html
    ![Experience Targeting Activity](assets/personalization-use-case-1/target-activity.png)
5. For **Virtual Experience Composer** to load, enable **Allow Load Unsafe scripts** on your browser and reload your page.
    ![Experience Targeting Activity](assets/personalization-use-case-1/load-unsafe-scripts.png)
6. Notice the WKND Site home page open in Virtual Experience Composer editor.
    ![VEC](assets/personalization-use-case-1/vec.png)  
7. To add an audience to your VEC, click on **Add Experience Targeting** under Audiences, and select the WKND-California audience and Click **Next**.
   ![VEC](assets/personalization-use-case-1/vec-select-audience.png)
8. Click on the WKND site page within VEC, select the HTML element to add the offer for WKND-California audience, and choose **Replace With** option and select the **HTML Offer**.
    ![Experience Targeting Activity](assets/personalization-use-case-1/vec-selecting-div.png)
9. Select the **WKND SkateFest California** HTML offer for the **WKND-California** audience from the offer select UI, and Click **Done**.
10. You should now be able to see the **WKND SkateFest California** HTML Offer added to your WKND Site page for the WKND-California audience.
11. Repeat steps 7-10 to add Experience Targeting for the other states and choose the corresponding HTML Offer.
12. Click **Next** to continue, and you can see a mapping for Audiences to Experiences
13. Click **Next** to move to Goals and Settings.
14. Choose your reporting source and identify a primary goal for your activity. For our use case, lets select the Reporting Source as **Adobe Target**, measuring activity as **Conversion**, action as viewed a page, and URL pointing to the WKND SkateFest Details page.
    ![Goal & Targeting - Target](assets/personalization-use-case-1/goal-metric-target.png)

    > [!NOTE]
    > You can also choose Adobe Analytics as your reporting source.

15. Hover over the current activity name and you can rename it to **WKND SkateFest - USA**, and then **Save and Close** your changes.
16. From the Activity details screen, make sure to **Activate** your activity.
    ![Activate Activity](assets/personalization-use-case-1/activate-activity.png)
17. Your WKND SkateFest Campaign is now live to all WKND Site visitors.
18. Navigate to the [WKND Site Home Page](http://localhost:4503/content/wknd/en.html) and you should be able to see the WKND SkateFest Offer based off your geolocation (*state: California*).
    ![Activity QA](assets/personalization-use-case-1/wknd-california.png)

### Target Activity QA {#marketer-activity-qa}

1. Under **Activity Details > Overview** tab, click on the **Activity QA** button and you can get the direct QA link to all your experiences.
    ![Activity QA](assets/personalization-use-case-1/activity-qa.png)
2. Navigate to the [WKND Site Home Page](http://localhost:4503/content/wknd/en.html) and you should be able to see the WKND SkateFest Offer based off your geolocation (state).
3. Watch the video below to understand how an offer gets delivered to your page, how to customize response tokens, and also perform a browser console quality check.

>[!VIDEO](https://video.tv.adobe.com/v/28658?quality=9)

## Summary {#Summary}

In this chapter, content editor was able to create all the content to support the WKND SkateFest campaign within Adobe Experience Manager and export it to Adobe Target as HTML Offers, for creating Experience Targeting, based off users geo location.
