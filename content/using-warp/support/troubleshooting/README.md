---
description: Resolve Common Issues with Warp
icon: wrench
---

# Troubleshooting

This section covers common issues you may encounter while using Warp and how to resolve them.

{% hint style="info" %}
Many issues can be diagnosed by reviewing your Runner Agent's log output. See [Troubleshooting Using a Runner Agent's Logs](../../migration-hq/runner-agent.md) for instructions on locating and reading logs.
{% endhint %}

## Quick Reference

| Issue | Symptoms | Likely Cause | Details |
| --- | --- | --- | --- |
| Failed Inventory Scan | Scan fails or no repos found | Permissions, expired PAT, outdated vault | [View guide](failed-inventory-scan.md) |
| Failed Migration | Migration action fails with error | Permissions, expired PAT, repo size limits | [View guide](failed-migration.md) |
| Main Branch Requirement | Runner Agent fails, no workflows run | Migration HQ default branch is not `main` | [View guide](main-branch-requirement.md) |
| Marketplace Installation | App not installed after Marketplace purchase | Webhook not delivered to Packfiles | [View guide](marketplace-installation-bypass.md) |

## Failed Inventory Scan

Inventory scans can fail when the credentials in your vault are expired, have insufficient permissions, or when the vault file is outdated. A GitHub outage can also prevent scans from running.

For detailed causes and resolution steps, see [Failed Inventory Scan](failed-inventory-scan.md).

## Failed Migration

Migrations can fail for many of the same reasons as inventory scans — expired or under-scoped credentials, outdated vault files, and GitHub outages. Additionally, repository size limitations and invalid destination repository names can cause migration failures.

For detailed causes and resolution steps, see [Failed Migration](failed-migration.md).

## Main Branch Requirement

Warp requires the Migration HQ repository's default branch to be named `main`. Organizations with a different default branch naming policy will experience runner failures until the branch is renamed.

For the resolution steps, see [Main Branch Requirement](main-branch-requirement.md).

## Marketplace Installation Bypass

In rare cases, installing Warp through the GitHub Marketplace may appear to succeed but the app is never installed. A direct installation link is available as a workaround.

For the resolution steps, see [Marketplace Installation Bypass](marketplace-installation-bypass.md).

## Still Need Help?

{% hint style="info" %}
If these guides don't resolve your issue, reach out to Product Support via the Support tab in your [Project](../../projects/README.md), or contact a [Packfiles Partner](../partners.md) for expert guidance.
{% endhint %}
