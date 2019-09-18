---
title: Activity Stream Essentials
seo-title: Activity Stream Essentials
description: List of recent activites performed by a member or a list of recent activities on a single thread of content
seo-description: List of recent activites performed by a member or a list of recent activities on a single thread of content
uuid: 2171c084-8fbe-4a71-a9ce-71c152c25e0e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d43d84ef-8de0-4c27-9399-c5343212bdf1
index: y
internal: n
snippet: y
---

# Activity Stream Essentials{#activity-stream-essentials}

The activities of a signed in community member, such as posting to a forum or blog, is collected into a stream which may be filtered and displayed in various ways through configuration of the activity streams component.

The ability to follow adds another set of activities when community members follow postings of interest or other community members.

All [community sites](../../../6-5/communities/using/overview.md#communitiessites) include a user profile page for the signed in member that will display member activities in the same manner.

## Concepts {#concepts}

An *activity stream* is the list of recent activities performed by a member or a list of recent activities on a single thread of content, such as a forum topic or blog.

A member my follow an activity stream, by either following another individual or content.

A *news feed* is a merging of the activity streams being followed by a member into a single stream.

A * [social graph](/6-5/communities/using/essentials-socialgraph.md)* captures the following relationships of one member to another.

## Essentials for Client-Side {#essentials-for-client-side}

<table border="1" cellpadding="4" cellspacing="4" width="100%"> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/activitystreams/components/hbs/activitystreams</td> 
  </tr>
  <tr>
   <td> <a href="/6-5/communities/using/scf.md#add-or-include-a-communities-component"><strong>includable</strong></a></td> 
   <td>No</td> 
  </tr>
  <tr>
   <td> <a href="../../../6-5/communities/using/clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.activitystreams</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/activitystreams.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity-title.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/clientlibs/activitystreams.css</td> 
  </tr>
  <tr>
   <td><strong> properties</strong></td> 
   <td>see <a href="../../../6-5/communities/using/activities.md">Activity Streams Feature</a></td> 
  </tr>
 </tbody>
</table>

* [Client-side Customizations](/6-5/communities/using/client-customize.md)

## Essentials for Server-Side {#essentials-for-server-side}

* [Activity Streams API](/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.md)

* [Activity Streams Listener API](/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.md)

* [Server-side Customizations](/6-5/communities/using/server-customize.md)

### Activity Stream Function {#activity-stream-function}

A community site structure that includes the [Activity Stream function](../../../6-5/communities/using/functions.md#activity-stream-function), includes a configured `activity streams` component.