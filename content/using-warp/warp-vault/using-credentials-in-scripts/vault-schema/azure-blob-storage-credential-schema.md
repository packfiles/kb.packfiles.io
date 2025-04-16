---
description: Azure Blob Storage Credential Schema v1.1.0
icon: cabinet-filing
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

# Azure Blob Storage Credential Schema

```
{
   "data" : {
      "azure_storage_connection_string" : "",
      "created_at" : "0001-01-01T00:00:00Z",
      "updated_at" : "0001-01-01T00:00:00Z",
      "uuid" : "8875afab-2f5f-4659-a627-330f86c40046"
   },
   "type" : "AzureBlobStorage",
   "uuid" : "8875afab-2f5f-4659-a627-330f86c40046"
}
```

#### Example Query

```
gh warp vault get '(type:AzureBlobStorage).azure_storage_connection_string'
```
