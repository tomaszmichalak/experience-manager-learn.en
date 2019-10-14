---
title: Capturing Error Messages in Form Data Model Service as Step in Workflow
seo-title: Capturing Error Messages in Form Data Model Service as Step in Workflow
description: Starting with AEM Forms 6.5.1, we now have the ability to capture error messages generated on using invoke Form Data Model Service as a step in AEM Workflow. Workflow.
seo-description: Starting with AEM Forms 6.5.1, we now have the ability to capture error messages generated on using invoke Form Data Model Service as a step in AEM Workflow. Workflow.
uuid: ecd5d5aa-01eb-48fb-872f-66c656ae14df.

feature: workflow
topics: integrations
audience: developer
doc-type: article
activity: setup
version: 6.5.1,6.5.2


---

# Capturing Error Messages in {#using-form-data-model-service-as-step-in-workflow}

Starting with AEM Forms 6.5.1,we now have the option to capture error messages and specify validation options. Invoke Form Data Model Service step has been enhanced to provide the following capabilities.

 * Providing an option for 3 tier validation  ("OFF" , "BASIC" and "FULL") to handle Exceptions encountered on invoking Form Data Model Service. The 3 options successively denote a stricter version of checking Database-specific requirements.
 
 * Providing a checkbox for customizing the execution of Workflow. Hence, user will now have the flexibility to go ahead with the Workflow Execution, even if Invoke Form Data Model step throws Exceptions.

 * Storing important information of Error arising due to validation exceptions. Three Autocomplete-type variable selectors have been incorporated to select relevant variables to store the ErrorCode(String), ErrorMessage(String) and ErrorDetails(JSON). The ErrorDetails however would be set to null incase the exception is not a DermisValidationException. 


