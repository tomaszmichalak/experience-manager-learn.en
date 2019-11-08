---
title: Trigger AEM workflow on HTM5 Form Submission
seo-title: Trigger AEM Workflow on HTML5 Form Submission
description: Continue filling mobile form in offline mode and submit mobile form to trigger AEM workflow
seo-description: Continue filling mobile form in offline mode and submit mobile form to trigger AEM workflow
feature: mobile-forms
topics: development
audience: developer
doc-type: article
activity: implement
version: 6.4,6.5
---

# Workflow to review and approve the submitted pdf

The last and final step of this use case is to create AEM workflow which will generate static or non-interactive pdf for review and approval. Workflow will be triggered via a launcher configured on the node /content/pdfsubmissions.
The following screen shot shows the steps involved in the workflow.

![workflow](assets/workflow.PNG)

## Generate Non-Interactive PDF workflow step

The xdp template and the data to be merged with the template is specified here. The data to be merged is the submitted data from the pdf. This submitted data is stored under the node /content/pdfsubmissions. 

![workflow](assets/generate-pdf1.PNG)

The generated pdf is assigned to workflow variable called submittedPDF

![workflow](assets/generate-pdf2.PNG)

### Assign the generated pdf for review and approval

Assign task workflow component is used here to assign the generated pdf for review and approval. The variable submittedPDF is used in the Forms and Documents tab of the Assign Task workflow component

![workflow](assets/assign-task.PNG)