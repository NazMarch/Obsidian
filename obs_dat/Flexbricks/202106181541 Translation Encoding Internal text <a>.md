#flexbricks 

For example Style->BOM->Bill of materials

There are grid with editable materials and material no is like a link.

If you need to translate something:

```ad-danger

title: Line_List_SKUPlan_Edit IT WAS

collapse: closed

```dotnet
htmlAnchor.InnerText = HttpUtility.UrlEncode(e.Item.DataItem("StyleNo").ToString)
```


```ad-success

title: Line_List_SKUPlan_Edit IT RIGHT

collapse: open

```dotnet
htmlAnchor.InnerText = e.Item.DataItem("StyleNo").ToString
```

Public Class Line_List_SKUPlan_Edit

```ad-success
title: SampleRequest_Workflow_Submit_Spec_Comment Right
collapse: open
```dotnet


internalCommentUrl.Text = String.Format(GetSystemTextHTML("Internal Comment {0}"), intCountInternalComments)

```
