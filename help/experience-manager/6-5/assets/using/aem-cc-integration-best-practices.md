---
title: AEM and Creative Cloud Integration Best Practices
seo-title: AEM and Creative Cloud Integration Best Practices
description: Best practices for integrating an AEM instance with Adobe Creative Cloud to streamline asset transfer workflows and achieve maximum efficiency.
seo-description: Best practices for integrating an AEM instance with Adobe Creative Cloud.
uuid: e1524d06-406d-46fc-8417-47921964987a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
discoiquuid: 622e033b-7bda-4d91-978b-ff1d2f87e735
index: y
internal: n
snippet: y
---

# AEM and Creative Cloud Integration Best Practices{#aem-and-creative-cloud-integration-best-practices}

<!--
Comment Type: remark
Last Modified By: Ashish Gupta . (asgupta)
Last Modified Date: 2019-06-04T04:02:36.225-0400
<p>This page is undergoing a major revamp given Adobe Asset Link is released at the same time as 6.5 GA. I have created a copy of previous content (referring to AEM to CC Folder Sharing; now deprecated) and saved it under <a href="/6-5/assets/using/aem-cc-integration-best-practices1.md">aem-cc-integration-best-practices1.html</a></p>
-->

Adobe Experience Manager (AEM) Assets is a digital asset management (DAM) solution that can integrate with Adobe Creative Cloud to help DAM users work together with creative teams, streamlining collaboration in the content creation process.

Adobe Creative Cloud provides creative teams with an ecosystem of solutions and services to help them to create digital assets. It includes desktop and mobile applications, cloud services like storage with desktop sync or web experience, as well as marketplaces like Adobe Stock.

Read on to know what integrations to pick between desktop and the enterprise-grade DAM based on your use case and what are the associated best practices for the connecting workflows.

>[!NOTE]
>
>AEM to Creative Cloud folder sharing is now deprecated and no longer covered below. Adobe recommend newer capabilities like Adobe Asset Link or AEM desktop app to provide creative users with access to the assets managed in AEM.

<!--
Comment Type: remark
Last Modified By: Ashish Gupta . (asgupta)
Last Modified Date: 2019-04-08T03:49:23.341-0400
<p><strong>Note2self</strong>: I think Key concepts should include this glossary. While this article is entirely conceptual, such content is more conceptual than other content. All such conceptual items should be collated below the actionable information.<br /> </p>
-->

## Collaboration need of creatives, marketers, and DAM users {#collaboration-need-of-creatives-marketers-and-dam-users}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody> 
  <tr> 
   <td style="text-align: center;">Requirements<br /> </td> 
   <td style="text-align: center;">Use case<br /> </td> 
   <td style="text-align: center;">Involved surfaces<br /> </td> 
  </tr> 
  <tr> 
   <td>Simplify experience for creatives on desktop</td> 
   <td>Streamline access to asset from a DAM (AEM Assets) for creative professionals, or more broadly, users on desktop working in native asset creation applications. They need an easy and straightforward way to discover, use (open), edit and save changes to AEM, as well as upload new files.</td> 
   <td>Win or Mac desktop; Creative Cloud apps<br /> </td> 
  </tr> 
  <tr> 
   <td>Provide high-quality, ready-to-use assets from Adobe Stock</td> 
   <td>Marketers help accelerate the content creation process by assisting with asset sourcing and discovery. Creative professionals use the approved assets right from within their creative tools.<br /> </td> 
   <td>AEM Assets; Adobe Stock marketplace; metadata fields<br /> </td> 
  </tr> 
  <tr> 
   <td>Distribute and share assets by organizations</td> 
   <td>Internal departments/local branches and external partners, distributors, and agencies use the approved assets shared by the parent organization. The organization wants to securely and seamlessly share the created assets for wider reuse.<br /> </td> 
   <td>Brand Portal, Asset Share Commons<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Adobe offerings to support the collaboration need {#adobe-offerings-to-support-the-collaboration-need}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody> 
  <tr> 
   <td style="text-align: center;">Value proposition for the involved personas</td> 
   <td style="text-align: center;">Adobe offering</td> 
   <td style="text-align: center;">Involved surfaces</td> 
  </tr> 
  <tr> 
   <td>Creative users discover assets from AEM, open and use them, edit and upload changes to AEM, as well as upload new files into AEM, without leaving Creative Cloud apps.</td> 
   <td><a href="https://helpx.adobe.com/enterprise/using/adobe-asset-link.html">Adobe Asset Link</a></td> 
   <td>Photoshop, Illustrator, and InDesign</td> 
  </tr> 
  <tr> 
   <td>Business users simplify opening and using assets, editing and uploading changes to AEM, and uploading new files into AEM from the desktop environment. They use a generic integration to open any asset type in the native desktop application, including non-Adobe ones.</td> 
   <td><a href="/desktop-app/aem-desktop-app.md">AEM desktop app</a><br /> </td> 
   <td>AEM desktop app on Win and Mac desktop</td> 
  </tr> 
  <tr> 
   <td>Marketers and business users discover, preview, license and save, and manage the Adobe Stock assets from within AEM. Licensed and saved assets provide select Adobe Stock metadata for better governance.</td> 
   <td><a href="../../../6-5/assets/using/aem-assets-adobe-stock.md">AEM and Adobe Stock integration</a></td> 
   <td>AEM web interface</td> 
  </tr> 
 </tbody> 
</table>

This article focuses primarily on the first two aspects of the collaboration needs. Distribution and sourcing of assets at scale is briefly mentioned as a use case. For such needs solutions, consider Adobe Brand Portal or Asset Share Commons. Alternate solutions such as [AEM Assets Brand Portal](/brand-portal/user-guide.md), solutions that can be built based on [Asset Share](../../../6-5/assets/using/assets-finder-editor.md) components, [Link Share](../../../6-5/assets/using/link-sharing.md), using [AEM Assets web UI](../../../6-5/assets/using/managing-assets-touch-ui.md) should be reviewed based on specific requirement.

![Creative Cloud connections for AEM: Deciding which capability to use](assets/creative-connections-aem.png)

Deciding on which capability to use

### Mapping of use cases and Adobe solutions {#mapping-of-use-cases-and-adobe-solutions}

<!--
Comment Type: remark
Last Modified By: Ashish Gupta . (asgupta)
Last Modified Date: 2019-06-04T07:52:53.824-0400
<p>Note2self: List the alternatives in overview of recommendations section. This section is just details of use case.</p>
<p>The other 2 bullet points are already covered above either in needs of creatives OR in the screenshot above.<br /> </p>
-->

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody> 
  <tr> 
   <th style="text-align: center;"><strong>Use Case</strong></th> 
   <th style="text-align: center;" width="127"><strong>Adobe Asset Link</strong></th> 
   <th style="text-align: center;" width="167"><strong>AEM desktop app</strong></th> 
   <th style="text-align: center;" width="201"><strong>Remarks / Other Solutions</strong></th> 
  </tr> 
  <tr> 
   <td style="text-align: left;">Discover - browse AEM folders</td> 
   <td style="text-align: left;">Yes</td> 
   <td style="text-align: left;">AEM Web UI + desktop actions</td> 
   <td style="text-align: left;">When browsing the network share, turn off the thumbnails to avoid downloading binary files of assets.<br /> </td> 
  </tr> 
  <tr> 
   <td style="text-align: left;">Discover - access AEM collections</td> 
   <td style="text-align: left;">Yes</td> 
   <td style="text-align: left;">AEM Web UI + desktop actions</td> 
   <td style="text-align: left;"> </td> 
  </tr> 
  <tr> 
   <td style="text-align: left;">Discover - search for assets from AEM</td> 
   <td style="text-align: left;">Yes</td> 
   <td style="text-align: left;">AEM Web UI + desktop actions</td> 
   <td style="text-align: left;"> </td> 
  </tr> 
  <tr> 
   <td style="text-align: left;">Use - open asset</td> 
   <td style="text-align: left;">Yes</td> 
   <td style="text-align: left;">Yes - for any app</td> 
   <td style="text-align: left;"><a href="../../../6-5/assets/using/managing-assets-touch-ui.md#previewing-assets">Open from Web UI</a> or from Finder</td> 
  </tr> 
  <tr> 
   <td height="21" style="text-align: left;">Use - place asset from AEM into a document</td> 
   <td style="text-align: left;">Yes - embedding</td> 
   <td style="text-align: left;">Yes - linking or embedding</td> 
   <td style="text-align: left;">AEM desktop app gives access to assets as files on the local file system. These links in the native apps are represented by local paths.</td> 
  </tr> 
  <tr> 
   <td height="43" style="text-align: left;">Edit - open for editing</td> 
   <td style="text-align: left;">Yes - Check-out action</td> 
   <td style="text-align: center;"><p style="text-align: left;">Yes - Open action (in the network share)</p> </td> 
   <td style="text-align: left;" width="201"><a href="https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html">Check-out in AAL</a> saves the asset to user's creative cloud storage account (synchronized by Creative Cloud app) by default. </td> 
  </tr> 
  <tr> 
   <td height="21" style="text-align: left;">Edit - work in progress outside AEM</td> 
   <td style="text-align: left;">Yes - Asset available in user's Creative Cloud storage account synced to desktop.</td> 
   <td style="text-align: left;">Possible - in version 1.10 there is an option to turn off automated upload of local changes to AEM.</td> 
   <td style="text-align: left;"> </td> 
  </tr> 
  <tr> 
   <td height="43" style="text-align: left;">Edit - upload changes</td> 
   <td style="text-align: left;">Yes - <a href="https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html">Check-in action</a> with optional comment</td> 
   <td style="text-align: left;">Yes</td> 
   <td width="201"><p style="text-align: left;"> </p> </td> 
  </tr> 
  <tr> 
   <td height="21" style="text-align: left;">Upload - single file</td> 
   <td style="text-align: left;">Yes - uploads current active document</td> 
   <td style="text-align: left;">Yes</td> 
   <td style="text-align: left;" width="201"><a href="../../../6-5/assets/using/managing-assets-touch-ui.md#uploading-assets">Web UI Upload</a></td> 
  </tr> 
  <tr> 
   <td height="64" style="text-align: left;">Upload - multiple files / hierarchical folder structures</td> 
   <td style="text-align: left;">No</td> 
   <td style="text-align: left;">Yes</td> 
   <td width="201"><p style="text-align: left;"><a href="../../../6-5/assets/using/managing-assets-touch-ui.md#uploading-assets">Web UI Upload</a></p> <p style="text-align: left;">Custom script / tool </p> </td> 
  </tr> 
  <tr> 
   <td height="21" style="text-align: left;">Misc - user and login</td> 
   <td style="text-align: left;">Creative Cloud user logged into Creative Cloud desktop app gets recognized (SSO)</td> 
   <td style="text-align: left;">AEM user / login</td> 
   <td style="text-align: left;">Users of both solutions count against the AEM user quota.</td> 
  </tr> 
  <tr> 
   <td height="21" style="text-align: left;">Misc - network and access</td> 
   <td style="text-align: left;">Requires access from user's desktop to AEM deployment over network</td> 
   <td style="text-align: left;">Requires access from user's desktop to AEM deployment over network<br /> <br /> </td> 
   <td style="text-align: left;">Adobe Asset Link does not share network proxy environment.<br /> </td> 
  </tr> 
  <tr> 
   <td height="21" style="text-align: left;">Misc - Migrate large number of assets</td> 
   <td style="text-align: left;">No<br /> <br /> </td> 
   <td style="text-align: left;">No<br /> <br /> </td> 
   <td style="text-align: left;"><a href="/6-5/assets/using/assets-migration-guide.md">Migration Guide</a></td> 
  </tr> 
 </tbody> 
</table>

To support asset distribution use cases, other solutions should be considered:

* [AEM Assets Brand Portal](/brand-portal/user-guide.md) for a configurable, SaaS add-on to AEM Assets to publish assets.  

* Custom solutions are created based on [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/) code base.
* AEM [link share](../../../6-5/assets/using/link-sharing.md) to share assets ad hoc using links.
* [AEM Assets web interface](../../../6-5/assets/using/managing-assets-touch-ui.md) with areas for external parties secured by AEM Access Control setup and with necessary IT / network configuration adjustments, giving these external users access to AEM.

## Key concepts and use cases {#key-concepts-and-use-cases}

### Glossary of common terms {#glossary-of-common-terms}

* **Work-in-progress or creative work-in-progress (WIP):** A phase in asset lifecycle where an asset undergoes multiple changes and is typically not yet ready to be shared with broader teams. 
* **Creative-ready assets:** Assets that are ready to be shared with a broader team, or have been  selected / approved  by the creative team for sharing with marketing or LOB teams.

* **Asset approvals:** The approval process that runs for assets already uploaded to DAM, which typically includes brand approvals, legal approvals, and so on.
* **Final asset:** An asset that has gone through all  approvals/metadata  tagging and is ready to be used by the broader team. Such an asset is stored in DAM and made available to all (or all interested) users. It can be used in marketing channels or by creative teams to create designs.

* **Minor asset  update/change :** A quick and small change to a digital asset. It is often made in response to a retouching or minor editing request, asset review, or approval (for example, reposition, change text size, adjust saturation/brightness, color, and so on).
* **Major asset  update/change :** A change to a digital asset that requires considerable work, and sometimes must be done over a longer period of time. It typically includes multiple changes. The asset must be saved multiple times while being updated. Major asset updates typically cause the asset to enter a WIP stage.
* **DAM:** Digital asset management. In this document, it is synonymous with AEM Experience Manager Assets, unless specifically mentioned otherwise.
* **Creative user:** A creative professional, who creates digital assets using Creative Cloud apps and services. In some cases, a creative user may be a member of a creative team who may use Creative Cloud, but does not create digital assets (like a creative director or creative team manager).
* ** DAM user: **A typical user of a DAM system. Depending on the organization, a DAM user can be a marketing or a non-marketing user, for example a Line-of-Business (LOB) user, librarian, sales person, and so on.

### Considerations when using AEM and Creative Cloud integration {#considerations-when-using-aem-and-creative-cloud-integration}

<!--
Comment Type: remark
Last Modified By: Ashish Gupta . (asgupta)
Last Modified Date: 2019-04-09T11:25:12.352-0400
<p>Note2self: Merge these in the use-case mapping table above.</p>
<p>If required, add a columns/info to include || User story || Adobe offering and its functionality || Conceptual info/Remarks ||</p>
-->

<!--
Comment Type: remark
Last Modified By: Ashish Gupta . (asgupta)
Last Modified Date: 2019-07-08T13:53:37.678-0400
<p>Mark a H2 about considerations and best practices.</p>
<p>In it make a table for various offerings and link to the individual best practices content.</p>
<ul>
<li>DA2.0 has it in troubleshooting.md file.</li>
<li>Stock integration article must have one sub-section now.</li>
<li>What about AAL?</li>
<li>What about BP?</li>
</ul>
-->

<!--
Comment Type: draft

<h3>Best practices and considerations when using integrations with AEM Assets</h3>
-->

* DA2.0 best practices: See troubleshooting.md
* Stock integration: See ?
* AAL: See ?
* BP: See ?

This is a brief summary of best practices for AEM & Creative Cloud Integration. Read the rest of this document to get the detailed understanding of these.

* **For creative users, working in Photoshop, InDesign, or Illustrator: **Adobe Asset Link provides the best user experience, including clean handling of the Work-in-progress on assets checked out from AEM
* **For simplifying access to assets from desktop for any generic file format or application: **use AEM desktop app
* **Understand why and when to store assets in DAM:** Updates to be made available to the broader team in your organization
* **Mind the volume of assets shared:** If your use case is asset distribution, governance and security might be the most important aspects. Consider using tools built for doing that at scale, like Brand Portal. 
* **Understand asset lifecycle: **Know how assets are handled in your organization by different teams
* **Handle frequent saves to assets with care: **Adobe Asset Link takes care of that for you with PS, AI, ID. For other applications, don't carry out work in progress tasks in mapped/shared folder unless you need all the changes in DAM

### Access to Adobe Stock assets from AEM Assets {#access-to-adobe-stock-assets-from-aem-assets}

<!--
Comment Type: remark
Last Modified By: Ashish Gupta . (asgupta)
Last Modified Date: 2019-06-17T10:15:42.230-0400
<p>Some of this content goves in the above tables and some of it in Stock best practices section in the article itself. Give a link to that section in the above tables:</p>
<ul>
<li>Top-level table of offering. and/or<br /> </li>
<li>Use case table in last Remarks column.</li>
</ul>
-->

[AEM and Adobe Stock integration](../../../6-5/assets/using/aem-assets-adobe-stock.md) provides AEM users with the ability to search, preview, license and save, assets from Adobe Stock into AEM. Licensed and saved Adobe Stock assets have selected Stock metadata, which can be used to search for them with extra filters.

A few important points about this integration:

* When assets from Adobe stock are saved to AEM, they become a regular AEM Assets, with binary saved to the AEM repository. Some metadata related to Adobe Stock are saved for the asset in AEM, otherwise the ingestion process looks the same as for any other file. For example, if Smart Tags are active, the tags are added to these assets upon saving.
* The asset saved to AEM is a copy, not a link back into Adobe Stock.

**Working with assets saved from Adobe Stock into AEM in Creative Cloud**. This integration is independent of Adobe Asset Link, but Adobe Asset Link recognizes these assets saved from Stock that way, and displays additional metadata and Stock icon on these assets in Adobe Asset Link extension UI in Photoshop, Illustrator, or InDesign. The files are available for browsing, opening, and so on - because they are regular AEM assets when saved to AEM.  
Creative users working in Creative Cloud apps with Adobe Asset Link extension present, in addition to having access to already-licensed assets from Adobe Stock into AEM, can also use Creative Cloud Libraries panel to search, preview, and license Adobe Stock assets.  
Assets from Adobe Stock licensed and saved into AEM become available to the broader teams accessing AEM Assets deployment, whereas creatives licensing assets from Adobe Stock via Creative Cloud Libraries panel make them available to themselves only by default in their Creative Cloud account.  

## About storing assets in a DAM {#about-storing-assets-in-a-dam}

To design an efficient workflow between creative and marketing/line-of-business (LOB) teams and choose the best support capabilities, it is important to understand when and why assets are stored in DAM.

#### Why assets are stored in DAM {#why-assets-are-stored-in-dam}

Storing assets in DAM makes them easily accessible and findable. It ensures that the assets can be leveraged by numerous users across the organization or ecosystem, which includes partners, customers, and so on.

Most organizations choose to only store assets that are relevant to the downstream marketing/LOB processes (publishing to channels like web channel via AEM Sites or other channels served by Adobe Experience Cloud - Marketing Cloud, Advertising Cloud, and measured by Analytics Cloud, providing to users/partners, and so on). In addition, organizations store assets that may be subjected to a review/approval process in DAM. This way, DAM stores mostly assets that have high chances of being leveraged, and avoids storing idle assets.

Storing assets is also subject to technical and resource utilization considerations. DAM provides additional services around stored assets, including extracting metadata, versioning, generating previews/transcoding, managing references, and adding access control information. These services consume additional time and infrastructure resources.

Often, storing all of the assets and updates is not desirable. For example, if updates to specific assets are of poor quality and consume excessive resources, the assets may not be stored in DAM.

#### When assets are stored in DAM {#when-assets-are-stored-in-dam}

Creative teams (and organizations) are usually not interested in storing assets at each stage of the asset lifecycle. For example, they avoid storing assets in the following cases:

* Assets that are yet to be finalized or are subject to experimentation
* Assets that fail to pass the creative/internal team review cycle
* Compared to the asset in question, the team has better candidates to represent their work to external teams

Usually, the following classes assets are stored in DAM:

* Assets that reached a certain maturity and are considered ready to be shared
* Assets that were pre-selected by the creative team
* Specific asset formats that are usable or requested by marketing, depending on a specific contract or agreement (for example, JPG files converted from RAW files, TIFFs/images from PSD originals)

#### When updates to assets are stored in DAM {#when-updates-to-assets-are-stored-in-dam}

As a rule, only updates to assets that are relevant to the broader set of DAM users should be stored in DAM. It ensures that users (marketing and similar functions) only see relevant versions in the DAM asset timeline.

Typically changes related to major milestones in the asset lifecycle. For example, the initial marketing-ready asset or an official update based on request/review provided by the creative team should be stored and versioned in DAM.

The creative team's update for review by the marketing team after a request for a change in the existing asset in DAM is an example of a relevant update. It should be stored and versioned in DAM for further reference or for reverting to the previous version.

The following are examples of updates that are typically not relevant:

* Early versions of assets uploaded before it is ready for marketing review
* Frequent creative changes to the asset in the work-in-progress phase before creative and marketing teams decide that the asset is ready

### User access to DAM {#user-access-to-dam}

AEM Assets supports two types of users based on their access to the AEM Assets deployment. Typically, users inside the enterprise network (firewall) have direct access to DAM. Other users outside the enterprise network would not have direct access. The user type determines which integrations can be used from the technical standpoint.

#### Creative users with direct access to DAM {#creative-users-with-direct-access-to-dam}

Typically, in-house creative teams or agencies/creative professionals  onboarded  to the internal network have access to the DAM instance, including AEM login. AEM and network infrastructure can be set up to allow direct access to external parties - usually trusted organizations like agencies working for a client - to have access to AEM over network (e.g., via VPN or IP whitelisting).

In such cases, Adobe Asset Link or AEM desktop app helps provide easy access to final/approved assets and lets you save creative-ready assets to DAM.

#### Creative users without access to DAM {#creative-users-without-access-to-dam}

External agencies and freelancers without direct access to the DAM instance may require access to approved assets or want to add their new designs to the DAM.

Use the following strategies to provide access to final/approved assets:

* Use desktop app if Asset Link does not work.  
* Use [AEM Assets Brand Portal](/brand-portal/user-guide.md) for distributing assets securely to external partners
* Use a custom implementation of a distribution and sourcing portal based on [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* Use Access Control set up in AEM and necessary network infrastructure (for example, VPN and IP whitelisting) to give external parties access to a dedicated area of content in your DAM. They can use AEM Web UI to get assets and upload new content into your DAM.

#### Work in progress on assets from AEM {#work-in-progress-on-assets-from-aem}

As discussed in this document, it is recommended to carry out major updates on assets, sometimes called work in progress, without having all the edits saved to the local file also uploaded to AEM as changes. This speeds up a desktop user's work, limit network bandwidth used, and keep the assets timeline clean and focused on controlled, major updates.

Adobe Asset Link offers a good support for this use case:

* When users in Photoshop, InDesign, or Illustrator intent to edit a file, they execute a Check-out operation on the given asset
* The asset is downloaded in background, put into users Creative Cloud account synchronized to disk by Creative Cloud desktop app, and the check-out flag is toggled in AEM on the asset to minimize editing conflicts
* From there on, the user works in a file that's stored locally in the synced location, and can continue working and saving necessary changes at any frequency required
* Additionally, because the asset is in the Creative Cloud account, it is also available on other devices that the user might have (for example, can be opened or edited in a dedicated Creative Cloud mobile app), and can be shared with other Creative Cloud users for collaboration purposes.
* When the creative user is done with the changes, they can execute a Check-in operation on that file in their Creative Cloud application, with an optional comment. The corresponding asset in AEM are versioned and updated to with the new binary. AEM users like Marketers or LOB users have access to major asset changes, or milestones, via AEM asset timeline UI.

AEM desktop app provides a network share for assets opened in the native app. By default, all the changes done locally are uploaded to AEM automatically after a brief while. With such a configuration, frequent saves during the work-in-progress phase would all be uploaded into AEM and versioned, creating a lot of network traffic and potential scalability challenges - not to mention unnecessary versions in AEM.

The recommended approach here is to use an option in AEM desktop app to turn off automated updates, and upload changes to assets to AEM manually, leveraging the upload changes action in the app's Asset Status UI.

#### Bulk upload to DAM {#bulk-upload-to-dam}

You may have a requirement to simultaneously upload a larger number of files into DAM in some scenarios, for example:

* Uploading results of  photoshoots  or larger projects
* Uploading assets provided by creative agencies
* Uploading selected assets from a larger set if the selection is done outside DAM

Note that this description refers to uploading files operationally (for example, every week or with every  photoshoot ), as a normal part of desktop user's workflow. Large asset migrations are not covered here.

You can leverage the following upload capabilities:

* To upload large/hierarchical folders in bulk, use AEM desktop app that provides [folder upload](/desktop-app/aem-desktop-app.md#bulkupload) functionality. You can also upload hierarchical folder structures. Assets are uploaded in background and, therefore, it is not tied to a web browser session
* To upload a few files from a single folder, drag the files directly to the web interface or use the Create option in the AEM Assets web interface.
* Depending upon your business requirements, you can also use custom uploaders.

#### Managing digital assets directly from desktop {#managing-digital-assets-directly-from-desktop}

If you use Network File Shares to manage digital assets, just using the network share mapped by AEM desktop app could be seen as a convenient substitute. When transitioning from network file shares, AEM web interface provides a rich set of Digital Asset Management capabilities that go well beyond what is possible on a network share (search, collections, metadata, collaboration, previews, and so on), and AEM desktop app provides a handy link to connect the server-side DAM repository with the work on desktop.

Avoid using AEM desktop app to manage assets directly in the network share of AEM Assets. For example, avoid using AEM desktop app to move/copy multiple files. Instead, use the AEM Assets web UI to drag folders from Finder/Explorer to the network share or use the AEM Assets Folder Upload feature.

#### Asset migration {#asset-migration}

To plan and execute asset migrations from existing system to a new system or migration of large volume of assets stored on servers, see the [Migration Guide](/6-5/assets/using/assets-migration-guide.md). AEM desktop app and AEM to Creative Cloud integrations do not support such migrations. Due to the large volumes of assets to be ingested, and additional requirements around metadata mapping, transformation, and ingestion, migrations should be handled using different tools and approaches.

<!--
<related-links>
<a href="https://helpx.adobe.com/enterprise/using/adobe-asset-link.html">Adobe Asset Link</a>
<a href="/desktop-app/aem-desktop-app-best-practices.md">AEM desktop app best practices</a>
<a href="/brand-portal/user-guide.md">AEM Brand Portal</a>
<a href="../../../6-5/assets/using/aem-assets-adobe-stock.md">AEM and Adobe Stock integration</a>
<a href="../../../6-5/assets/using/aem-cc-folder-sharing-best-practices.md">AEM to Creative Cloud folder sharing best practices</a>
</related-links>
-->
