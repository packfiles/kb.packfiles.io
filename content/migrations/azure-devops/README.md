---
description: Learn about Warp's Support for Azure DevOps Services
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

# Azure DevOps

<figure><img src="../../.gitbook/assets/image (7) (1) (1) (1) (1) (1).png" alt="" width="375"><figcaption></figcaption></figure>

This document provides an overview of Warp's capabilities for migrating data from Azure DevOps Services to GitHub products.&#x20;

Warp does not provide a migration path for Azure DevOps Server, only Azure DevOps Services. To migrate from Azure DevOps Server, you'll need to [migrate to Azure DevOps Services](https://azure.microsoft.com/en-us/services/devops/migrate/) first.

### Repository Data

Warp includes built in support for [data migrated by GitHub Enterprise Importer](https://docs.github.com/en/migrations/using-github-enterprise-importer/migrating-from-azure-devops-to-github-enterprise-cloud/about-migrations-from-azure-devops-to-github-enterprise-cloud), including:

* Repository contents and Git history,&#x20;
* Pull requests, including
  * User history,
  * Work item links, and&#x20;
  * Attachments
* Branch policies
  * User-scoped branch policies and cross-repository branch policies are not included.

For specific information about the limitations on the types and size of data that can be migrated, refer to the [Limitations](limitations.md) page in this section.

### Azure Pipelines

Warp is capable of "rewiring" Azure Pipelines associated with repositories in your source Azure DevOps environment. Rewiring modifies the pipeline to associate it with the migrated copy of your repository in GitHub, rather than the original repository in Azure DevOps.

Rewiring enables a flexible path to GitHub adoption, enabling further migration processes (for instance, re-creating your existing pipelines with GitHub Actions) to proceed incrementally. Your team can enjoy the experience of hosting their code and development process on GitHub, while retaining the flexibility to continue using their existing pipelines until they're ready to replace them with Actions.

To facilitate the pipeline rewiring process, Warp will [automatically share and normalize service connections](service-connections.md) for the Azure Pipelines GitHub App.

### Azure Boards

If you have installed and connected the [Azure Boards GitHub App](https://learn.microsoft.com/en-us/azure/devops/boards/github/install-github-app?view=azure-devops) to your destination GitHub Organization, Warp can configure this integration for your migrated GitHub repositories with the [/integrate-boards](../../using-warp/slash-commands/azure-devops/integrate-boards.md) slash command.

#### Autolink References for Work Items

In addition to integrating Azure Boards, Warp is also capable of configuring GitHub's [Autolink References](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/configuring-autolinks-to-reference-external-resources) feature with the [/autolink-work-items](../../using-warp/slash-commands/azure-devops/autolink-work-items.md) slash command.&#x20;

When this integration is enabled, references to Azure Boards work items in issues, pull requests, commit messages, and release descriptions will automatically become clickable hyperlinks to the work item they reference.

### Post-Migration Tasks

Warp supports a variety of utility slash commands for Azure DevOps to automate common tasks like locking or disabling the original repository when a migration has been completed. These are listed in the [Azure DevOps section](../../using-warp/slash-commands/azure-devops/) of our slash command documentation.

Warp additionally supports slash commands for common post-migration tasks such as adding teams in GitHub to a repository with specific permissions. Documentation for these commands can be located in our [slash commands guide](../../using-warp/slash-commands/).

