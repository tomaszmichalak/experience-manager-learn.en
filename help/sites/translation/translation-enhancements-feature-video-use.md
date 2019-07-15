---
title: Translation Enhancements in AEM
seo-title: Translation Enhancements in AEM
description: AEM's robust translation framework allows AEM content to be seamlessly translated by supported Translation vendors.
seo-description: AEM's robust translation framework allows AEM content to be seamlessly translated by supported Translation vendors.
uuid: ad3c8210-0eff-4a01-8d26-4b35be161377
contentOwner: allee
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: administering
discoiquuid: 2039effd-628f-4df6-a1c6-a33092518273
targetaudience: target-audience ongoing;target-audience new
index: y
internal: n
snippet: y
---

# Translation Enhancements with Multi-Site Manager {#translation-enhancements}

AEM's robust translation framework allows AEM content to be seamlessly translated by supported Translation vendors.

## Translation Enhancements in AEM 6.5

>[!VIDEO](https://video.tv.adobe.com/v/27405?quality=9)

AEM 6.5 translation enhancements includes:

**Auto-approve translation jobs**: The approval flag in the translation job is a binary property. It does not drive or integrate with out-of-the-box review and approval workflows. To keep the number of steps in a translation job minimal,  It is by default set to "automatically approve" in Advanced Properties of a Translation Project. If your organization requires approval for a translation job, you can uncheck the "automatically approve" option in Advanced Properties of a Translation Project.

**Automatically delete translation launches**: Rather than manually deleting translation launches in Launches Admin after the fact, it is now possible to automatically delete translation launches after they were promoted.

**Export Translation objects in JSON format**: AEM 6.4 and earlier versions support XML and XLIFF formats of translations objects. You can now configure the export format to JSON format using your systems console Config Manager. Look for Translation Platform Configuration, and then you can select the export format as JSON.

**Update translated AEM content in Translation Memory (TMS)**: local author who does not have access to AEM can make updates to translated content, that was already ingested back into AEM, directly in the TM (Translation Memory, in TMS), and to update the translations in AEM by resending translation job from TMS to AEM

## Translation Enhancements in AEM 6.4

>[!VIDEO](https://video.tv.adobe.com/v/21309?quality=9)

Authors can now quickly and easily create multi-language translation projects directly from either the Sites admin or the Projects admin, set up those projects to automatically promote launches, and even set schedules for automation.

## Additional Resources {#additional-resources}

* [Translating Content for Multilingual Sites](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/translation.html)
* [https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/tc-manage.html](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/tc-manage.html)
* [Translation Best Practices](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/tc-bp.html)