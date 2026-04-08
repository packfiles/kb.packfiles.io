---
description: Resolve Issues with Failed Inventory Scans
icon: magnifying-glass
---

# Failed Inventory Scan

An inventory scan is how Warp discovers repositories in your source platform. When you run a scan, Warp's Runner Agent connects to your source (Azure DevOps, Bitbucket Server, etc.) using the credentials stored in your vault and retrieves a list of repositories. This page covers the reasons an inventory scan can fail and how to resolve them.

## Symptoms

* Scan action fails in the Actions tab of Migration HQ.
* Scan completes but no repositories appear in the Issues tab.
* Error messages in runner logs referencing authentication or authorization.

## Common Causes and Solutions

### Insufficient Permissions

The personal access token (PAT) stored in your vault may not have the scopes required to read repositories from your source platform.

**Resolution:**

1. Verify the PAT has the required scopes for your source platform. Refer to the [Set Up Your Vault](../../../guides/quickstart/set-up-your-vault.md) guide for the specific scopes needed.
2. If the scopes are incorrect, generate a new PAT with the correct permissions.
3. Update the credential in the Warp Vault app and push the updated vault file to Migration HQ.

### Expired Personal Access Token

Personal access tokens have expiration dates. An expired PAT will cause authentication failures during the scan.

**Resolution:**

1. Check the expiration date of the PAT on your source platform.
2. Generate a new PAT with the same scopes.
3. Update the credential in the [Warp Vault](../../warp-vault/README.md) app and push the updated vault file to Migration HQ.

### Outdated Vault File

If credentials were updated outside of Warp Vault, or a new vault was generated but not pushed to Migration HQ, the vault file may be stale.

**Resolution:**

1. Open the [Warp Vault](../../warp-vault/README.md) app and verify your credentials are current.
2. Re-export the vault file.
3. Push the updated `vault.age` file to Migration HQ.

### GitHub Outage

If GitHub is experiencing an outage, Runner Agents cannot execute workflows, and scans will fail.

**Resolution:**

1. Check [GitHub Status](https://www.githubstatus.com/) for any ongoing incidents.
2. Wait for the incident to be resolved, then retry the scan.

## Checking Runner Logs

Runner Agent logs provide detailed error information that can help identify the root cause. See [Troubleshooting Using a Runner Agent's Logs](../../migration-hq/runner-agent.md) for instructions on locating and reading log output.

## Related Pages

* [Failed Migration](failed-migration.md) — similar causes apply to migration failures
* [Troubleshooting](README.md) — index of all common issues
* [Support](../README.md) — contact Product Support
