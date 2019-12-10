---
title: Getting Started with AEM Sites - WKND Tutorial
seo-title: Getting Started with AEM Sites - WKND Tutorial
description: Getting Started with AEM Sites - WKND Tutorial. The WKND tutorial is a multi-part tutorial designed for developers new to Adobe Experience Manager. The tutorial walks through the implementation of an AEM site for a fictitious lifestyle brand, the WKND. The tutorial covers fundamental topics like project setup, Core Components, Editable Templates, client libraries, and component development.
seo-description: Getting Started with AEM Sites - WKND Tutorial. The WKND tutorial is a multi-part tutorial designed for developers new to Adobe Experience Manager. The tutorial walks through the implementation of an AEM site for a fictitious lifestyle brand, the WKND. The tutorial covers fundamental topics like project setup, Core Components, Editable Templates, client libraries, and component development.
uuid: 4b369f63-858c-4c26-b092-a3151b53924a
products: SG_EXPERIENCEMANAGER/6.5/SITES
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: developing
discoiquuid: a0c5006a-7777-45e4-aca7-560a42fd6e56
targetaudience: target-audience new
mini-toc-levels: 1
index: y
---

# Getting Started with AEM Sites - WKND Tutorial {#introduction}

Welcome to a multi-part tutorial designed for developers new to Adobe Experience Manager (AEM). This tutorial walks through the through the implementation of an AEM site for a fictitious lifestyle brand the WKND. The tutorial covers fundamental topics like project setup, Core Components, Editable Templates, client libraries, and component development with Adobe Experience Manager Sites.

## WKND Tutorial Overview {#wknd-tutorial-overview}

The goal for this multi-part tutorial is to teach a developer how to implement a website using the latest standards and technologies in Adobe Experience Manager (AEM). After completing this tutorial a developer understands the basic foundation of the platform and has knowledge of common design patterns in AEM.

>[!VIDEO](https://video.tv.adobe.com/v/27305?quality=9)

The implementation works as-is on **AEM 6.5** and **AEM 6.4.2+**. Many of the topics apply to all versions of AEM. The site is implemented using:

* [Maven AEM Project Archetype](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)
* [Core Components](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html)
* [HTL](https://docs.adobe.com/content/help/en/experience-manager-htl/using/getting-started/getting-started.html)
* Sling Models
* [Editable Templates](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/page-authoring/template-editor-feature-video-use.html)
* [Style System](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/page-authoring/style-system-feature-video-use.html)

*Estimate 1-2 hours to get through each part of the tutorial.*

## About the tutorial {#about-tutorial}

The WKND is a fictional online magazine and blog that focuses on nightlife, activities, and events in several international cities. To make this tutorial closer to a real-world scenario one of Adobe's talented UX designers created the mockups for the site. Over the course of the tutorial various pieces of the mockup are implemented into a fully author-able AEM site. Special thanks to **Lorenzo Buosi** and **Kilian Amendola** who created the beautiful design for the WKND site.

The name WKND is fitting because we expect a developer to take the better part of a ***weekend*** to complete the tutorial.

### Reference Site {#reference-site}

A finished version of the WKND Site is also available as a reference. The tutorial covers the major development skills needed for an AEM developer but will not build the entire site end-to-end. The finished reference site is another great resource to explore and see more of AEM's out of the box capabilities.

To test the latest code before jumping into the tutorial, download and install the [latest release from GitHub](https://github.com/adobe/aem-guides-wknd/releases/latest).

### Github {#github}

All of the code for the project can be found on Github in the AEM Guide repo:

**[GitHub: WKND Sites Project](https://github.com/adobe/aem-guides-wknd)**

In addition, each part of the tutorial has its own branch in GitHub. A user can begin the tutorial at any point by simply checking out the branch that corresponds to the previous part.

## Local Development Environment {#local-dev-environment}

A local development environment is necessary to complete this tutorial. Screenshots and video are captured from a Mac OS environment but the commands and code used should be independent of the local operating system, unless otherwise noted.

**New to AEM?** Check out the [following guide to setting up a local development environment](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html).

### Required software

The following should be installed:

* [AEM 6.5](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/technical-requirements.html) or [AEM 6.4 + SP2](https://helpx.adobe.com/experience-manager/6-4/release-notes/sp-release-notes.html)
* [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/index.html) or [Java 11](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html) (AEM 6.5+ only)
* [Apache Maven](https://maven.apache.org/) (3.3.9 or newer)
* [Node.js v10+](https://nodejs.org/en/)
* [npm 6+](https://www.npmjs.com/)
* [Git](https://git-scm.com/)

### Integrated Development Environment (IDE)

This tutorial uses [Eclipse](https://www.eclipse.org/) with the [AEM Developer Tool Plugin](https://eclipse.adobe.com/aem/dev-tools/) as the IDE, however any IDE that has support for Java and Maven projects can be used. The reliance on specific IDE features in this tutorial is minimal.

For detailed steps for using Eclipse or any other IDE for [local development with AEM check out the following guide](https://docs.adobe.com/content/help/en/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html).

## Table of Contents {#table-of-contents}

*Estimate 1-2 hours to get through each part of the tutorial.*

### Chapter 1 {#chapter-1}

**[Project Setup](project-setup.md)** - Covers the creation of a Maven Multi Module Project to manage the code and configurations for an AEM Site.

#### Maven, Eclipse IDE, Core Components, SCM, and Github

### Chapter 2 {#chapter-2}

**[Creating a Base Page and Template](pages-templates.md)** - Covers the creation of a base page and an editable template. Core Component proxies are inspected.

#### Editable Templates, Core Components, Content Authoring

### Chapter 3 {#chapter-3}

**[Client-Side Libraries and Responsive Grid](client-side-libraries.md)** - Covers creation of AEM Client-Side Libraries or clientlibs to deploy and manage CSS and Javascript for an AEM Sites implementation. Integration with AEM's responsive grid and mobile emulator. [aemfed](https://aemfed.io/) module is used to accelerate front end development.

#### Client-Side Libraries, CSS, Javascript, LESS, aemfed, Responsive Grid

### Chapter 4 {#chapter-4}

**[Developing with the Style System](style-system.md)** - Covers extending Core Components with brand-specific CSS and leveraging the Style System to create multiple variations of components. This part also uses Content Fragments for long form article content and covers some advanced policy configurations of the Template Editor.

#### CSS, Style System, Template Editor Policies

### Chapter 5 {#chapter-5}

**[Creating a custom AEM Component](custom-component.md)** - Covers the end to end creation of a custom byline component that displays authored content. Includes developing a Sling Model to encapsulate business logic to populate the byline component and corresponding HTL to render the component.

#### Sling Models, HTL, Style System, Custom Components

### Chapter 6 {#chapter-6}

**[Unit Testing](unit-testing.md)** - Covers the implementation of a Unit Test that validates the behavior of the Byline component's Sling Model, created in [Chapter 5](custom-component.md) of the tutorial.

#### Unit tests, io.wcm AEM Mocks, Mockito and JUnit

### Chapter 7 {#chapter-7}

**[Header and Footer](header-footer.md)** - Covers dynamic navigation driven by the content hierarchy and fixed navigation populated by content authors. Sling Models, HTL templating language, and dialogs are used to implement the Header and Footer navigation. A Quick Search component is also added to the Header.

#### HTL, Design Dialogs, Composite Components

### Chapter 8 {#chapter-8}

**[Landing Page](landing-page.md)** - Covers the implementation of the Teaser and Carousel components to populate a dynamic and exciting Homepage.

#### Advanced Template Editor Policies, Style System, Teaser and Carousel components
