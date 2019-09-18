---
title: Content Fragments Support in AEM Assets HTTP API
seo-title: Content Fragments Support in AEM Assets HTTP API
description: Learn about Content Fragments Support in AEM Assets HTTP API.
seo-description: Learn about Content Fragments Support in AEM Assets HTTP API.
uuid: 1559b731-3318-4110-ac5c-a60f7ad6be14
contentOwner: aheimoz
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
topic-tags: extending-assets
discoiquuid: 41753d3c-6311-4933-bd25-a05610cacb9d
index: y
internal: n
snippet: y
---

# Content Fragments Support in AEM Assets HTTP API{#content-fragments-support-in-aem-assets-http-api}

<!--
Comment Type: remark
Last Modified By: Alison Heimoz (aheimoz)
Last Modified Date: 2019-03-13T08:59:18.934-0400
<p>Based on:</p>
<ul>
<li><a href="https://wiki.corp.adobe.com/pages/viewpage.action?pageId=1570187152">https://wiki.corp.adobe.com/pages/viewpage.action?pageId=1570187152</a></li>
</ul>
<p>There are some additional comments there too.<br /> </p>
-->

## Overview {#overview}

>[!NOTE]
>
>The [Assets HTTP API](../../../6-5/assets/using/mac-api-assets.md) encompasses the:
>
>* Assets REST API >
>    * including support for Content Fragments
>
>The current implementation of AEM Assets HTTP API is REST.

The Adobe Experience Manager (AEM) [Assets REST API](../../../6-5/assets/using/mac-api-assets.md) allows developers to access content (stored in AEM) directly over the HTTP API, via CRUD operations (Create, Read, Update, Delete).

The API allows you to operate AEM as a headless CMS (Content Management System) by providing Content Services to a JavaScript front end application. Or any other application that can execute HTTP requests and handle JSON responses.

For example, Single Page Applications (SPA), framework-based or custom, require content provided over the HTTP API, often in JSON format.

While AEM Core Components provide a very comprehensive, flexible and customizable API that can serve required Read operations for this purpose, and whose JSON output can be customized, they do require AEM WCM (Web Content Management) know-how for implementation as they must be hosted in (API) pages that are based on dedicated AEM templates. Not every SPA development organization has access to such resources.

This is when the Assets REST API can be used. It allows developers to access assets (for example, images and content fragments) directly, without need to first embed them in a page, and deliver their content in serialized JSON format. (Note that it is not possible to customize JSON output from the Assets REST API). The Assets REST API also allows developers to modify content - by creating new, updating, or deleting existing assets, content fragments and folders.

The Assets REST API:

* follows the [HATEOAS principle](https://en.wikipedia.org/wiki/HATEOAS)   

* implements the [SIREN format](https://github.com/kevinswiber/siren)

## Prerequisites {#prerequisites}

The Assets REST API is available on each out-of-the-box install of a recent AEM version.

## Key Concepts {#key-concepts}

The Assets REST API offers [REST](https://en.wikipedia.org/wiki/Representational_state_transfer)-style access to assets stored within an AEM instance. It uses the `/api/assets` endpoint and requires the path of the asset to access it (without the leading `/content/dam`).

The HTTP method determines the operation to be executed:

* **GET** - to retrieve a JSON representation of an asset or a folder
* **POST** - to create new assets or folders
* **PUT** - to update the properties of an asset or folder
* **DELETE** - to delete an asset or folder

>[!NOTE]
>
>The request body and/or URL parameters can be used to configure some of these operations; for example, define that a folder or an asset should be created by a **POST** request.

The exact format of supported requests is defined in the [API Reference](../../../6-5/assets/using/assets-api-content-fragments.md#api-reference) documentation.

### Transactional Behavior {#transactional-behavior}

All requests are atomic.

This means that subsequent ( `write`) requests cannot be combined into a single transaction that could succeed or fail as a single entity.

### AEM (Assets) REST API versus AEM Components {#aem-assets-rest-api-versus-aem-components}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody> 
  <tr> 
   <td>Aspect</td> 
   <td>Assets REST API<br /> </td> 
   <td>AEM Component<br /> (components using Sling Models)</td> 
  </tr> 
  <tr> 
   <td>Supported use-case(s)</td> 
   <td>General purpose.</td> 
   <td><p>Optimized for consumption in a Single Page Application (SPA), or any other (content consuming) context.</p> <p>Can also contain layout information.</p> </td> 
  </tr> 
  <tr> 
   <td>Supported operations</td> 
   <td><p>Create, Read, Update, Delete.</p> <p>With additional operations depending on the entity type.</p> </td> 
   <td>Read-only.</td> 
  </tr> 
  <tr> 
   <td>Access</td> 
   <td><p>Can be accessed directly.</p> <p>Uses the <span class="code">/api/assets </span>endpoint, mapped to <span class="code">/content/dam</span> (in the repository).</p> <p>For example, to access:<code class="code">
       /content/dam/we-retail/en/experiences/arctic-surfing-in-lofoten</code><br /> request:<br /> <span class="code">/api/assets/we-retail/en/experiences/arctic-surfing-in-lofoten.model.json</span></p> </td> 
   <td><p>Needs to be referenced through an AEM component on an AEM page.</p> <p>Uses the <span class="code">.model</span> selector to create the JSON representation.</p> <p>An example URL would look like:<br /> <span class="code">http://localhost:4502/content/we-retail/language-masters/en/experience/arctic-surfing-in-lofoten.model.json</span></p> </td> 
  </tr> 
  <tr> 
   <td>Security</td> 
   <td><p>Multiple options are possible.</p> <p>OAuth is proposed; can be configured separately from standard setup.</p> </td> 
   <td>Uses AEM's standard setup.</td> 
  </tr> 
  <tr> 
   <td>Architectural remarks</td> 
   <td><p>Write access will typically address an author instance.</p> <p>Read may also be directed to a publish instance.</p> </td> 
   <td>As this approach is read-only, it will typically be used for publish instances.</td> 
  </tr> 
  <tr> 
   <td>Output</td> 
   <td>JSON-based SIREN output: verbose, but powerful. Allows for navigating within the content.</td> 
   <td>JSON-based proprietary output; configurable through Sling Models. Navigating the content structure is hard to implement (but not necessarily impossible).</td> 
  </tr> 
 </tbody> 
</table>

### Security {#security}

If the Assets REST API is used within an environment without specific authentication requirements, AEM's CORS filter needs to be configured correctly.

>[!NOTE]
>
>For further information see:
>
>* [CORS/AEM explained](/kt/platform-repository/using/cors-security-article-understand.md)
>* [Video - Developing for CORS with AEM](/kt/platform-repository/using/cors-security-technical-video-develop.md)
>

<!--
Comment Type: remark
Last Modified By: Alison Heimoz (aheimoz)
Last Modified Date: 2019-03-13T08:59:31.031-0400
<p>OAuth is still an open issue for the security docs - disparate info received so far. Alexandru is raising the matter with Arun.</p>
<p>Apparently the Gems session doesn't mention Assets, and the sound quality is very bad.<br /> </p>
-->

In environments with specific authentication requirements, OAuth is recommended.

<!--
Comment Type: draft

<p>In environments with specific authentication requirements, OAuth is recommended. To configure please see this <a href="/kt/eseminars/gems/aem-oauth-server-functionality-in-aem.md">Gem session</a>. Additional information is available under <a href="/kt/platform-repository/using/oauth-code-sample-develop.md">OAuth scopes</a>.</p>
-->

## Available Features {#available-features}

Content Fragments are a specific type of Asset, see [Working with Content Fragments](../../../6-5/assets/using/content-fragments.md).

For further information about features available through the API see:

* [Available Features](../../../6-5/assets/using/mac-api-assets.md#available-features) of the Assets REST API
* [Entity Types](../../../6-5/assets/using/assets-api-content-fragments.md#entity-types)

### Paging {#paging}

The Assets REST API supports paging (for GET requests) via the URL parameters:

* `offset` - the number of the first (child) entity to retrieve
* `limit` - the maximum number of entities returned

The response will contain paging information as part of the `properties` section of the SIREN output. This `srn:paging` property contains the total number of (child) entities ( `total`), the offset and the limit ( `offset`, `limit`) as specified in the request.

>[!NOTE]
>
>Paging is typically applied on container entities (i.e. folders or assets with renditions), as it relates to the children of the requested entity.

#### Example: Paging {#example-paging}

`GET /api/assets.json?offset=2&limit=3`

```
...
"properties": {
    ...
    "srn:paging": {
        "total": 7,
        "offset": 2,
        "limit": 3
    }
    ...
}
...
```

## Entity Types {#entity-types}

### Folders {#folders}

Folders act as containers for assets and other folders. They reflect the structure of the AEM content repository.

The Assets REST API exposes access to the properties of a folder; for example its name, title, etc. Assets are exposed as child entities of folders.

>[!NOTE]
>
>Depending on the asset type the list of child entities may already contain the full set of properties that defines the respective child entity. Alternatively, only a reduced set of properties may be exposed for an entity in this list of child entities.

### Assets {#assets}

If an asset is requested, the response will return its metadata; such as title, name and other information as defined by the respective assets schema.

The binary data of an asset is exposed as a SIREN link of type `content` (also known as the `rel attribute`).

Assets can have multiple renditions. These are typically exposed as child entities, one exception being a thumbnail rendition, which is exposed as a link of type `thumbnail` ( `rel="thumbnail"`).

### Content Fragments {#content-fragments}

A [content fragment](../../../6-5/assets/using/content-fragments.md) is a special type of asset. They can be used to access structured data, such as texts, numbers, dates, amongst others.

As there are several differences to *standard* assets (such as images or audio), some additional rules apply to handling them.

#### Representation {#representation}

Content fragments:

* Do not expose any binary data.   
* Are completely contained in the JSON output (within the `properties` property).   

* Are also considered atomic, i.e. the elements and variations are exposed as part of the fragment's properties vs. as links or child entities. This allows for efficient access to the payload of a fragment.

#### Content Models and Content Fragments {#content-models-and-content-fragments}

Currently the models that define the structure of a content fragment are not exposed through an HTTP API. Therefore the *consumer* needs to know about the model of a fragment (at least a minimum) - although most information can be inferred from the payload; as data types, etc. are part of the definition.

To create a new content fragment, the (internal repository) path has to be provided.

#### Associated Content {#associated-content}

Associated content is currently not exposed.

## Using {#using}

Usage can differ depending on whether you are using an AEM author or publish environment, together with your specific use case.

* Creation is strictly bound to an author instance ([and currently there is no means to replicate a fragment to publish using this API](../../../6-5/assets/using/assets-api-content-fragments.md#limitations)).  

* Delivery is possible from both, as AEM serves requested content in JSON format only.

    * Storage and delivery from an AEM author instance should suffice for behind-the-firewall, media library applications.
    * For live web delivery, an AEM publish instance is recommended.

>[!CAUTION]
>
>The dispatcher configuration on AEM cloud instances might block access to `/api`.

<!--
Comment Type: remark
Last Modified By: Alison Heimoz (aheimoz)
Last Modified Date: 2019-03-13T09:54:53.110-0400
<p>6.5 - CHECK LINK FOR REFERENCE MATERIAL</p>
-->

>[!NOTE]
>
>For further details, see the [API Reference](../../../6-5/assets/using/assets-api-content-fragments.md#api-reference). In particular, [Adobe Experience Manager Assets API - Content Fragments](/6-5/sites/developing/using/reference-materials/assets-api-content-fragments/index.md).

### Read/Delivery {#read-delivery}

Usage is via:

`GET /{cfParentPath}/{cfName}.json`

For example:

[http://localhost:4502/api/assets/we-retail/en/experiences/arctic-surfing-in-lofoten.json](http://localhost:4502/api/assets/we-retail/en/experiences/arctic-surfing-in-lofoten.json)

The response is serialized JSON with the content structured as in the content fragment. References are delivered as reference URLs.

Two types of read operations are possible:

* Reading a specific content fragment by path, this returns the JSON representation of the content fragment.  
* Reading a folder of content fragments by path: this returns the JSON representations of all content fragments within the folder.

### Create {#create}

Usage is via:

`POST /{cfParentPath}/{cfName}`

The body has to contain a JSON representation of the content fragment to be created, including any initial content that should be set on the content fragment elements. It is mandatory to set the `cq:model` property and it must point to a valid content fragment model. Failing to do so will result in an error. It is also necessary to add a header `Content-Type` which is set to `application/json`.

### Update {#update}

Usage is via

`PUT /{cfParentPath}/{cfName}`

The body has to contain a JSON representation of what is to be updated for the given content fragment.

This can simply be the title or description of a content fragment, or a single element, or all element values and/or metadata. It is also mandatory to provide a valid `cq:model` property for updates.

### Delete {#delete}

Usage is via:

`DELETE /{cfParentPath}/{cfName}`

## Limitations {#limitations}

There are a few limitations:

* **Variations cannot be written and updated.** If those variations are added to a payload (e.g. for updates) they will be ignored. However, the variation will be served via delivery ( `GET`).  

* **Content fragment models are currently not supported**: they cannot be read or created. To be able to create a new, or update an existing, content fragment, developers have to know the correct path to the content fragment model. Currently the only method to get an overview of these is through the administration UI.
* **References are ignored**. Currently there are no checks on whether an existing content fragment is referenced. Therefore, for example, deleting a content fragment might result in issues on a page that contains a reference.

<!--
Comment Type: remark
Last Modified By: Alison Heimoz (aheimoz)
Last Modified Date: 2019-03-22T00:23:17.063-0400
<p>Original from wiki - in draft only mode.</p>
-->

<!--
Comment Type: draft

<ul>
<li><strong>Validation of create/update payload</strong> is limited.</li>
<li><strong>No validation of metadata</strong> against the metadata schema. This validation is missing in the Assets implementation and therefore not available here. Any metadata will be written, but might not be visible in the UI (only in CRXDE).</li>
<li><strong>A specific variation cannot be retrieved in isolation</strong>. The entire content fragment is returned.<br /> </li>
<li><strong>Variations cannot be written and updated.</strong> However, the variation will be served via delivery (<span class="code">GET</span>). If those variations are added to a payload (e.g. for updates) they will be ignored.</li>
<li><strong>Content fragment models are currently not supported</strong>: they cannot be read or created. To be able to create a new, or update an existing, content fragment, developers have to know the correct path to the content fragment model. Currently the only method to get an overview of these is through the administration UI.</li>
<li><strong>References are ignored</strong>. Currently there are no checks on whether an existing content fragment is referenced. Therefore, for example, deleting a content fragment might result in issues on a page that contains a reference.</li>
<li><strong>Replication of content fragments</strong>. A content fragment created on an author instance has to be replicated manually, or by other means.</li>
<li><strong>Errors status codes</strong> of the API might be misleading, see <a href="../../../6-5/assets/using/assets-api-content-fragments.md#status-codes-and-error-messages">Status Codes and Error Messages</a>.</li>
<li>The administration UI does not use this specific API.</li>
</ul>
-->

## Status Codes and Error Messages {#status-codes-and-error-messages}

The following status codes can be seen in the relevant circumstances:

1. 202 (OK)

   Returned when:

    * requesting a content fragment via `GET`  
    
    * successfully updating a content fragment via `PUT`

1. 201 (Created)

   Returned when:

    * successfully creating a content fragment via `POST`

1. 404 (Not found)

   Returned when:

    * the requested content fragment does not exist

1. 500 (Internal server error)

   <!--
   Comment Type: remark
   Last Modified By: Alison Heimoz (aheimoz)
   Last Modified Date: 2019-03-20T07:45:29.121-0400
   <p>Not standard for this error code</p>
   -->

   >[!NOTE]
   >
   >This error is returned:
   >
   >    
   >    
   >    * when an error that cannot be identified with a specific code has happened  
   >    * when the given payload was not valid
   >    
   >

   The following lists common scenarios when this error status is returned, together with the error message (monospace) generated:

    * Parent folder does not exist (when creating a content fragment via `POST`)
    * No content fragment model is supplied (null value), resource is null (potentially a permission problem) or the resource is no valid fragment template:

        * `No content fragment model specified`
        * `Cannot create a resource of given model '/foo/bar/qux'`
        * `Cannot adapt the resource '/foo/bar/qux' to a content fragment template`

    * The content fragment could not be created (potentially a permission problem):

        * `Could not create content fragment`

    * Title and or description could not be updated:

        * `Could not set value on content fragment`

    * Metadata could not be set:

        * `Could not set metadata on content fragment`

    * Content element could not be found or could not be updated

        * `Could not update content element`
        * `Could not update fragment data of element`

   The detailed error messages are usually returned in the following manner:

   ```xml
   {
     "class": "core/response",
     "properties": {
       "path": "/api/assets/foo/bar/qux",
       "location": "/api/assets/foo/bar/qux.json",
       "parentLocation": "/api/assets/foo/bar.json",
       "status.code": 500,
       "status.message": "...{error message}.."
     }
   }
   ```

## API Reference {#api-reference}

<!--
Comment Type: remark
Last Modified By: Alison Heimoz (aheimoz)
Last Modified Date: 2019-01-30T07:10:37.897-0500
<p>6.5 - CHECK LINK FOR REFERENCE MATERIAL</p>
-->

See here for detailed API references:

* [Adobe Experience Manager Assets API - Content Fragments](/6-5/sites/developing/using/reference-materials/assets-api-content-fragments/index.md)
* [Assets HTTP API](../../../6-5/assets/using/mac-api-assets.md)

    * [Available Features](../../../6-5/assets/using/mac-api-assets.md#available-features)

## Additional Resources {#additional-resources}

For further information see:

* [Assets HTTP API documentation](../../../6-5/assets/using/mac-api-assets.md)
* [AEM Gem session: OAuth](/kt/eseminars/gems/aem-oauth-server-functionality-in-aem.md)

<!--
Comment Type: remark
Last Modified By: Alison Heimoz (aheimoz)
Last Modified Date: 2018-12-13T02:46:13.040-0500
<p>need public link to complete<br /> </p>
-->

<!--
Comment Type: draft

<p>For further information see:</p>
<ul>
<li><a href="../../../6-5/assets/using/mac-api-assets.md">Assets HTTP API documentation</a></li>
<li><a href="/kt/eseminars/gems/aem-oauth-server-functionality-in-aem.md">AEM Gem session: OAuth</a></li>
<li>HAF Extensibility</li>
</ul>
-->
