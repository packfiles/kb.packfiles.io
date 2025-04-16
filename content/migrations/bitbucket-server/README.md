---
description: Learn about Warp's Support for Bitbucket Server
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

# Bitbucket Server

<figure><img src="../../.gitbook/assets/Bitbucket@2x-blue.png" alt="" width="375"><figcaption></figcaption></figure>

This document provides an overview of Warp's capabilities for migrating data from Bitbucket Server to GitHub products.

{% hint style="info" %}
Warp does not provide a migration path for Bitbucket Cloud. Only Bitbucket Server is supported.
{% endhint %}

Warp includes built in support for [data migrated by GitHub Enterprise Importer](https://docs.github.com/en/migrations/using-github-enterprise-importer/migrating-from-azure-devops-to-github-enterprise-cloud/about-migrations-from-azure-devops-to-github-enterprise-cloud), including:

* Repository contents and Git history,
* Pull requests, including
  * Comments,&#x20;
  * Pull request reviews,
  * Pull request review comments (both at the file and line level)
  * Required reviewers, and
  * Attachments

For specific information about the limitations on the types and size of data that can be migrated, refer to the [Limitations](limitations.md) page in this section.

#### Post-Migration Tasks <a href="#post-migration-tasks" id="post-migration-tasks"></a>

Warp supports a variety of utility slash commands for common post-migration tasks such as adding teams in GitHub to a repository with specific permissions. Documentation for these commands can be located in our [slash commands guide](https://kb.packfiles.io/using-warp/slash-commands).
