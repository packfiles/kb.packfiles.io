---
icon: bitbucket
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

# Bitbucket Server Credential Schema

```
{
   "data" : {
      "created_at" : "0001-01-01T00:00:00Z",
      "credentials" : {
         "password" : "",
         "username" : ""
      },
      "disable_ssl_verification" : false,
      "host_configuration" : {
         "archive_download_host" : "",
         "shared_home_directory" : "",
         "smb_domain" : "",
         "smb_password" : "",
         "smb_username" : "",
         "ssh_key" : "",
         "ssh_port" : 0,
         "ssh_username" : ""
      },
      "host_platform" : "",
      "storage_configuration" : {
         "migration_storage_provider_uuid" : "",
         "migration_storage_type" : ""
      },
      "updated_at" : "0001-01-01T00:00:00Z",
      "url" : "",
      "uuid" : "d27cb06d-0a7d-4ffa-8d9a-85ec646ecd35"
   },
   "type" : "BitbucketServer",
   "uuid" : "d27cb06d-0a7d-4ffa-8d9a-85ec646ecd35"
}
```

#### Example Query

```
gh warp vault get '(type:BitbucketServer).credentials.password'
```
