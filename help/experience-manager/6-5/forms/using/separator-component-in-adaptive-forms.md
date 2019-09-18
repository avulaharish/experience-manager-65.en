---
title: Separator component in adaptive forms
seo-title: Separator component in adaptive forms
description: You can use the separator component to visually segregate sections of a form.
seo-description: You can use the separator component to visually segregate sections of a form.
uuid: 3b04ee0e-a65d-4b32-a26b-00f4bb6b897d
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 70522093-5ee4-442f-a7a6-347e4278ae3c
index: y
internal: n
snippet: y
---

# Separator component in adaptive forms{#separator-component-in-adaptive-forms}

You can use the separator component to visually segregate panels of a form. You can define the overall appearance and style of a separator component by specifying the following properties of separator component:

* **Element Name:** Specifies the name of the component. The SOM expressions addresses the component with value specified in the Element Name field.
* **Thickness:** ** **Specifies the thickness of the separator component in pixels.

* **CSS Class:** Specifies the custom CSS class for the separator component  

* **Inline styles: **With AEM Forms, you can now apply inline CSS styles to individual adaptive form components and preview the changes in real-time.

You can use the Layout mode to define the number of columns that the separator component spans to. For more information, see [Use Layout mode to resize components](../../../6-5/forms/using/resize-using-layout-mode.md).

To specify properties of a separator component:

1. Select a separator component and tap ![](assets/cmppr.png). The properties open in sidebar.
1. Click a tab in the Inline CSS Properties section to specify CSS properties. For example: a. In the Field tab, click **Add Item**. A row with two fields gets added.
1. In the first field from left, specify a CSS3 property you want to apply. For example, **border**. You can also select a property by clicking the down-arrow button. The drop-down list is not exhaustive and you can specify any supported CSS3 property name in this field.
1. In the adjoining field, specify a valid value for the specified CSS3 property. For example, **3px solid black**.
1. Click **Add Item **to specify another property and its value.
1. Click **Preview **to preview the changes in the form.
1. Click **OK **to confirm the changes or **Cancel **to exit the dialog without any changes.

<!--
<related-links>
<a href="../../../6-5/forms/using/introduction-forms-authoring.md">Introduction to authoring adaptive forms</a>
</related-links>
-->
