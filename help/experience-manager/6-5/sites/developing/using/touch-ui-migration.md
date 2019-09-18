---
title: Migration to the Touch UI
seo-title: Migration to the Touch UI
description: Migration to the Touch UI
seo-description: Migration to the Touch UI
uuid: 5a14b9cf-6090-4d7c-b972-50a0c90202bf
contentOwner: aheimoz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: introduction
discoiquuid: 7e1e3312-ff55-4878-a052-853da5883bb8
index: y
internal: n
snippet: y
---

# Migration to the Touch UI{#migration-to-the-touch-ui}

<!--
Comment Type: remark
Last Modified By: Alison Heimoz (aheimoz)
Last Modified Date: 2019-07-04T02:01:03.059-0400
<p>Related to: <a href="https://jira.corp.adobe.com/browse/CQDOC-9996">https://jira.corp.adobe.com/browse/CQDOC-9996</a></p>
<p>Content based on: <a href="https://wiki.corp.adobe.com/display/~meyer/Touch+UI+-+Migration+Guide">https://wiki.corp.adobe.com/display/~meyer/Touch+UI+-+Migration+Guide</a></p>
-->

Starting with version 6.0, Adobe Experience Manager (AEM) introduced a new user interface referred to as the *touch-enabled UI* (also known simply as the *touch UI*). It is aligned to the Adobe Marketing Cloud and to the overall Adobe user interface guidelines. This has become the standard UI in AEM with the legacy, desktop-oriented interface referred to as the *classic UI*.

If you have been using AEM with classic UI you will need to take action to migrate your instance. This page is intended to act as a springboard by providing links to individual resources.

>[!NOTE]
>
>Such a migration project may have significant impact on your instance. See [Managing Projects - Best Practices](../../../../6-5/managing/using/best-practices.md) for recommended guidelines.

## The Basics {#the-basics}

When migrating you should be aware of the following (major) differences between the classic and touch UI:

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody> 
  <tr> 
   <td>Classic UI</td> 
   <td>Touch-Enabled UI</td> 
  </tr> 
  <tr> 
   <td>Is described in the JCR repository as a structure of nodes. Every node that represents an element of the UI is called an <em>ExtJS widget</em> and rendered on the client-side by <span class="code">ExtJS</span>.</td> 
   <td>Also described in the JCR repository as a structure of nodes. However, in this case every node refers to a Sling resource type (Sling component), that is in charge of its rendering. So the UI is (basically) rendered server-side.</td> 
  </tr> 
  <tr> 
   <td><p><span class="code">sling:resourceType</span></p> 
    <ul> 
     <li>not used</li> 
    </ul> </td> 
   <td><span class="code">sling:resourceType</span> 
    <ul> 
     <li>used</li> 
     <li>for example<br /> <span class="code">cq/gui/components/authoring/dialog</span><br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Dialog nodes:</p> 
    <ul> 
     <li>Name: <span class="code">dialog</span></li> 
     <li>jcr:primaryType: <span class="code">cq:Dialog</span></li> 
    </ul> </td> 
   <td><p>Dialog nodes:</p> 
    <ul> 
     <li>Name: <span class="code">cq:dialog</span></li> 
     <li>jcr:primaryType: <span class="code">nt:unstructured</span></li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Javascript location:</p> 
    <ul> 
     <li>Imperative parts are directly embedded using listeners or managed in clientlibs.</li> 
    </ul> </td> 
   <td><p>Javascript location:</p> 
    <ul> 
     <li>Imperative parts cannot be embedded in dialog definition; separation of responsibilities.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Event handling:</p> 
    <ul> 
     <li>Dialog widgets directly reference Javascript code.</li> 
    </ul> </td> 
   <td><p>Event handling:</p> 
    <ul> 
     <li>Javascript observes dialog events.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Rendering done by the client: 
    <ul> 
     <li>Client dynamically creates the UI components.</li> 
     <li>Client requests (Pull) component definition (as JSON) from server.</li> 
    </ul> </td> 
   <td>Rendering done by the server: 
    <ul> 
     <li>Client requests pages together with the related UI.</li> 
     <li>The server sends (Push) the UI as HTML documents; using Coral UI components.<br /> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

In other words, migrating a section of your UI from the classic UI to the touch UI means porting an *ExtJS widget* to a *Sling component*. To ease this, the touch UI is based on the Granite UI framework, which already provides some Sling components for the UI (referred to as Granite UI components).

Before you start, check the status and related recommendations:

* [Touch UI Features Status](../../../../6-5/release-notes/touch-ui-features-status.md)
* [User Interface Recommendations for Customers](../../../../6-5/sites/deploying/using/ui-recommendations.md)

The basics of developing the touch UI will provide a solid basis:

* [Concepts of the AEM Touch-Enabled UI](../../../../6-5/sites/developing/using/touch-ui-concepts.md)
* [Structure of the AEM Touch-Enabled UI](/6-5/sites/developing/using/touch-ui-structure.md)

## Migrating Page Authoring {#migrating-page-authoring}

Dialogs are a major factor when migrating your components:

<!--
Comment Type: remark
Last Modified By: Alison Heimoz (aheimoz)
Last Modified Date: 2019-07-02T08:03:44.390-0400
<p>is the dialog converter still relevant?</p>
<p>will it work if they've made additional customizations?</p>
-->

* [Developing AEM Components](../../../../6-5/sites/developing/using/developing-components.md) (with the touch-enabled UI)
* [Migrating from a Classic Component](../../../../6-5/sites/developing/using/developing-components.md#migrating-from-a-classic-component)
* [Dialog Conversion Tool](/6-5/sites/developing/using/dialog-conversion.md) - to help you convert the dialogs of your classic UI components to touch UI

    * There is a compatibility layer in touch UI to open a classic UI dialog within a "Touch UI wrapper", but this has limited functionality and is not recommended for the long-term.

* [Customizing Dialog Fields in Touch UI](/kt/eseminars/gems/aem-customizing-dialog-fields-in-touch-ui.md)
* [Creating a New Granite UI Field Component](/6-5/sites/developing/using/granite-ui-component.md)
* [Customizing Page Authoring](/6-5/sites/developing/using/customizing-page-authoring-touch.md) (with the touch-enabled UI)

## Migrating Consoles {#migrating-consoles}

<!--
Comment Type: remark
Last Modified By: Alison Heimoz (aheimoz)
Last Modified Date: 2019-07-02T08:01:53.797-0400
<p>the links are about customization</p>
<p>is there anything to be done for migrating if they never customized anything in classic?</p>
-->

You can also costomize the consoles:

* [Customizing the Consoles](../../../../6-5/sites/developing/using/customizing-consoles-touch.md) (for the touch-enabled UI)

## Related Considerations {#related-considerations}

Although not directly related to a migration to the touch UI, there are related issues that are worth considering at the same time, as they are also recommended practice:

* [Templates](/6-5/sites/developing/using/templates.md) - [Editable templates](../../../../6-5/sites/developing/using/page-templates-editable.md)  

* [Core Components](/core-components/user-guide.md)
* [HTL](/htl/user-guide.md)

>[!NOTE]
>
>See also [Developing - Best Practices](/6-5/sites/developing/using/best-practices.md).

## Further Resources {#further-resources}

<!--
Comment Type: remark
Last Modified By: Alison Heimoz (aheimoz)
Last Modified Date: 2019-07-04T03:12:55.152-0400
<p>version dependent<br /> </p>
-->

For full information on developing AEM see the collection of resources under:

* [Developing User Guide](/6-5/sites/developing/user-guide.html?topic=/experience-manager/6-5/sites/developing/morehelp/introduction.ug.js)
* [Granite UI Documentation](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/index.html)
* [AEM 6.5 Sites Tutorials and Videos](/kt/sites/index/aem-6-5-sites.md)
* [Getting Started Developing AEM Sites - WKND Tutorial](../../../../6-5/sites/developing/using/getting-started.md)
* [AEM Gems](/kt/eseminars/gems/aem-index.md)
* [AEM Modernization Tools](http://opensource.adobe.com/aem-modernize-tools/)

>[!CAUTION]
>
>AEM Modernization Tools are a community effort and are not supported or warrantied by Adobe.
