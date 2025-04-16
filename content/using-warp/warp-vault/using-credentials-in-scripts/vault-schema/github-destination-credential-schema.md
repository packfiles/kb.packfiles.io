---
description: GitHub (Destination) Credential Schema v1.1.0
icon: square-github
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

# GitHub (Destination) Credential Schema

```
{
   "data" : {
      "created_at" : "0001-01-01T00:00:00Z",
      "destination_type" : "ghec | ghec_emu | ghec_dr",
      "expiration_days" : 0,
      "ghec_dr_domain" : "",
      "organization_slug" : "",
      "pat" : "",
      "updated_at" : "0001-01-01T00:00:00Z",
      "uuid" : "d469e3f3-1937-4a1c-8fc2-2237a4efdf13"
   },
   "type" : "GitHubDestination",
   "uuid" : "d469e3f3-1937-4a1c-8fc2-2237a4efdf13"
}
```

#### Example Query

```
gh warp vault get '(type:GitHubDestination).pat'
```
