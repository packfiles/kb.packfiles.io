---
description: Resolve Runner Failures Caused by Branch Naming Policies
icon: code-branch
---

# Main Branch Requirement

Warp requires the Migration HQ repository's default branch to be named `main`. If your GitHub organization enforces a different default branch name (e.g., `master`, `develop`, `trunk`), the Warp Runner Agent will fail to execute.

## Symptoms

* Runner Agent fails immediately after any Warp operation.
* No workflow runs appear in Migration HQ's Actions tab, or they fail during setup.
* Warp does not respond to slash commands.

## Cause

Warp's runner workflows are configured to execute on the `main` branch. GitHub organizations can set an organization-level default branch naming policy that overrides the default for all new repositories. When this policy is set to something other than `main`, the Migration HQ repository is created with a different default branch name, and Warp's workflows cannot run.

## Resolution

1. Navigate to the Migration HQ repository on GitHub.
2. Go to **Settings** > **General**.
3. Under **Default branch**, change the branch name to `main`.

{% hint style="info" %}
If your organization enforces a branch naming policy, you can temporarily change the organization-level default to `main` before installing Warp. Once the Migration HQ repository is created with `main` as its default branch, you can change the organization-level policy back. The Migration HQ repository will retain `main` as its default branch.
{% endhint %}

## Prevention

Before installing Warp, verify that either:

* Your organization's default branch naming policy is set to `main`, or
* You are prepared to manually change the Migration HQ repository's default branch to `main` after it is created.

## Related Pages

* [Failed Migration](failed-migration.md) — other causes of migration failures
* [Failed Inventory Scan](failed-inventory-scan.md) — other causes of scan failures
* [Troubleshooting](README.md) — index of all common issues
