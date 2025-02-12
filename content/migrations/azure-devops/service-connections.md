---
icon: plug-circle-check
description: Warp Automatically Shares Service Connections for Azure Pipelines
---

# Service Connections

To facilitate the rewiring of Azure Pipelines, Warp automatically manages the sharing of [service connections](https://learn.microsoft.com/en-us/azure/devops/pipelines/library/service-endpoints?view=azure-devops) for the [Azure Pipelines GitHub App](https://github.com/apps/azure-pipelines).

Before rewiring Azure Pipelines, the service connection ID of the Azure Pipelines GitHub App must be configured in your Project's [Warp.yml](../../using-warp/migration-hq/warp.yml.md).

After configuring the service connection ID, Warp will automatically share the App's service connection with any Team Project where it is not already present.&#x20;

When Azure Pipelines service connections are shared, Warp normalizes the name for your convenience to ensure it matches the name of your destination GitHub organization.&#x20;

<figure><img src="../../.gitbook/assets/image (8) (1) (1) (1).png" alt="A shared Azure Pipelines service connection created automatically by Warp." width="276"><figcaption><p>A shared Azure Pipelines service connection created by Warp.</p></figcaption></figure>

