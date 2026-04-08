---
description: Resolve Issues with Failed Migrations
icon: triangle-exclamation
---

# Failed Migration

When you run a migration, Warp uses GitHub's migration APIs to move repository data from your source platform to GitHub. This page covers the reasons a migration can fail and how to resolve them.

## Symptoms

* Migration action fails in the Actions tab of Migration HQ.
* Warp posts an error comment on the repository's issue in Migration HQ.
* The issue comment includes a **Troubleshoot** section with a link to runner logs.

## Common Causes and Solutions

### Insufficient Permissions

The personal access token (PAT) used for the destination GitHub organization may lack the required scopes, or the Warp GitHub App installation may be missing permissions.

**Resolution:**

1. Verify the destination PAT has the required scopes. Refer to the [Set Up Your Vault](../../../guides/quickstart/set-up-your-vault.md) guide for the specific scopes needed.
2. Verify the Warp GitHub App has the necessary permissions on the destination organization.
3. If scopes are incorrect, generate a new PAT, update the credential in the [Warp Vault](../../warp-vault/README.md) app, and push the updated vault file to Migration HQ.

### Expired Personal Access Token

Personal access tokens have expiration dates. An expired PAT will cause authentication failures during migration.

**Resolution:**

1. Check the expiration date of the PAT on both your source and destination platforms.
2. Generate a new PAT with the same scopes.
3. Update the credential in the [Warp Vault](../../warp-vault/README.md) app and push the updated vault file to Migration HQ.

### Outdated Vault File

If credentials were updated outside of Warp Vault, or a new vault was generated but not pushed to Migration HQ, the vault file may be stale.

**Resolution:**

1. Open the [Warp Vault](../../warp-vault/README.md) app and verify your credentials are current.
2. Re-export the vault file.
3. Push the updated `vault.age` file to Migration HQ.

### Repository Size Limitations

GitHub's migration APIs have size limits for repository data. Very large repositories may exceed these limits.

**Resolution:**

1. Review the limitations for your source platform: [Azure DevOps Limitations](../../../migrations/azure-devops/limitations.md) or [Bitbucket Server Limitations](../../../migrations/bitbucket-server/limitations.md).
2. Consider reducing repository size before migration (e.g., removing large binary files from history).

### Invalid Destination Repository Name

Certain repository naming constraints on GitHub may cause the migration to fail (e.g., names ending in `.wiki` are not permitted).

**Resolution:**

1. Use the [`/rename-destination`](../../slash-commands/migration/rename-destination.md) slash command to change the destination repository name before retrying the migration.

### GitHub Outage

If GitHub is experiencing an outage, Runner Agents cannot execute workflows, and migrations will fail.

**Resolution:**

1. Check [GitHub Status](https://www.githubstatus.com/) for any ongoing incidents.
2. Wait for the incident to be resolved, then retry the migration.

## Checking Runner Logs

Runner Agent logs provide detailed error information that can help identify the root cause. See [Troubleshooting Using a Runner Agent's Logs](../../migration-hq/runner-agent.md) for instructions on locating and reading log output.

## Related Pages

* [Failed Inventory Scan](failed-inventory-scan.md) — similar causes apply to scan failures
* [Main Branch Requirement](main-branch-requirement.md) — runner failures caused by branch naming
* [Troubleshooting](README.md) — index of all common issues
* [Support](../README.md) — contact Product Support
