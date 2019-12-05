---
title: Acroforms with AEM Forms
seo-title: Merge Adaptive Form data with Acroform
feature: adaptive-forms
topics: development
audience: developer
doc-type: tutorial
activity: implement
version: 6.3,6.4
---

# Create Schema from the acroform

The next step is to create a schema from the Acroform created in the earlier step. A sample application is provided to create the schema as part of this tutorial. To create the schema, please follow the following instructions:

* Login to [crx](http://localhost:4502/crx/de)
* Navigate to /apps/AemFormsSamples/components/createxsd/POST.jsp
* change the saveLocation to an appropriate folder on your hard drive. Make sure the folder you are saving to is already created.
* Point your browser to [createXSD](http://localhost:4502/content/DocumentServices/CreateXsd.html).
* Drag and drop the acroform.
* Check the folder specified in point 3. The schema file is saved to this location.

## Upload the Acroform

For this demo to work on your system, you will need to create a folder called "acroforms" in assets. Upload the acroform into this acroforms folder

>[!NOTE]
The sample code looks for the acroform in this folder. The acroform is needed to merge the adaptive form's submitted data