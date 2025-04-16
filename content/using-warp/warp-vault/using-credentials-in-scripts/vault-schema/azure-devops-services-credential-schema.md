---
description: Azure DevOps Services Credential Schema v1.1.0
icon: microsoft
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# Azure DevOps Services Credential Schema

```
{
   "data" : {
      "access_scope" : "global",
      "created_at" : "0001-01-01T00:00:00Z",
      "expiration_days" : 30,
      "organization_slug" : "",
      "pat" : "",
      "updated_at" : "0001-01-01T00:00:00Z",
      "uuid" : "5a8f91e4-14a3-4129-8e5b-c0f50b4cc096"
   },
   "type" : "AzureDevOps",
   "uuid" : "5a8f91e4-14a3-4129-8e5b-c0f50b4cc096"
}
```

#### Example Query

```
gh warp vault get '(type:AzureDevOps).pat'
```
