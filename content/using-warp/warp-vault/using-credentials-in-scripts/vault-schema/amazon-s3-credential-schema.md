---
description: Amazon S3 Credential Schema v1.1.0
icon: bucket
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

# Amazon S3 Credential Schema

```
{
   "data" : {
      "aws_access_key_id" : "",
      "aws_region" : "",
      "aws_secret_access_key" : "",
      "bucket_name" : "",
      "created_at" : "0001-01-01T00:00:00Z",
      "updated_at" : "0001-01-01T00:00:00Z",
      "uuid" : "3d934d71-2166-47e1-b396-69714a979d29"
   },
   "type" : "AmazonS3",
   "uuid" : "3d934d71-2166-47e1-b396-69714a979d29"
}
```

#### Example Query

```
gh warp vault get '(type:AmazonS3).bucket_name'
```
