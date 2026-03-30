---
icon: shield-check
description: Control who can execute commands with issue and slash command policies.
---

# Access Policies

Access policies let you control who can run Warp commands in your _Migration HQ_ repository. You configure them in the `policies` section of your [`warp.yml`](warp.yml.md) file.

## How Policies Work

Warp uses an **opt-in security model**. By default — when no policies are defined — all organization members have full access to run any command. Once you define a policy, Warp switches to a restrictive mode where **only the users and teams you specify are allowed to act**.

This means:

* **No policies defined:** All organization members can run all commands.
* **Policies defined:** Only explicitly approved users and teams can run commands that match a policy.

There are two types of policies: **issue policies** and **slash command policies**. You can use them independently or together.

## Issue Policies

Issue policies control who can run slash commands on Backlog Issues based on the issue's labels. Define them under `policies.issues` in your `warp.yml`.

### How Label Matching Works

1. When a user runs a command on an issue, Warp checks the issue's labels against your configured policies.
2. If any labels match, only the users and teams listed in matching policies can run the command.
3. If no labels match any issue policy, then no access is granted to that issue by issue policies; the command can still run only if a matching slash command policy explicitly allows it.

Each issue policy has:

* **A unique identifier** — an internal reference name for the policy.
* **`labels`** (optional) — a list of issue labels that trigger this policy. If omitted, the policy applies globally to all issues.
* **`teams`** (optional) — GitHub team slugs granted access.
* **`users`** (optional) — GitHub usernames granted access.

When multiple policies match an issue (through overlapping labels or a global policy), their allowed users and teams are **combined** — a user permitted by any matching policy is allowed.

### Example: Limit Access by Label

Restrict commands on issues labeled with a specific Azure DevOps (ADO) team to only members of the corresponding GitHub team:

```yaml
policies:
  issues:
    onboarding:
      labels: ["ado:team:catball-inc"]
      teams: ["catball-inc-team"]
      users: ["chaserx", "johndoe"]
```

In this example, only members of the `catball-inc-team` GitHub team and the users `chaserx` and `johndoe` can run commands on issues that have the `ado:team:catball-inc` label.

### Example: Grant Global Access

Create a policy without labels to grant access across all issues, regardless of their labels:

```yaml
policies:
  issues:
    global_access:
      teams: ["release-engineering", "dev-ops"]
      users: ["admin-user"]
```

This gives the `release-engineering` and `dev-ops` teams, along with `admin-user`, access to run commands on every issue.

### Combining Label and Global Policies

You can define both label-specific and global policies. When an issue is evaluated, Warp combines the allowed users and teams from all matching policies — including any global policy — to determine access.

```yaml
policies:
  issues:
    global_access:
      teams: ["release-engineering"]
    platform_team:
      labels: ["ado:team:platform"]
      teams: ["platform-engineering"]
      users: ["team-lead"]
```

For an issue labeled `ado:team:platform`, both the `release-engineering` team (from the global policy) and the `platform-engineering` team and `team-lead` user (from the label-specific policy) are allowed.

## Slash Command Policies

Slash command policies control access to specific commands across all issues. Define them under `policies.slash_commands` in your `warp.yml`.

> **Important:** When you define any slash command policy, Warp denies access to all commands by default. Only the commands you explicitly configure are available.

Each slash command policy is keyed by the command name (starting with `/`) and specifies which teams and users can run it.

### Example: Restrict a Single Command

```yaml
policies:
  slash_commands:
    /migrate:
      teams: ["release-engineering"]
      users: ["chaserx"]
```

Only members of `release-engineering` and the user `chaserx` can run `/migrate`. All other slash commands are denied because a slash command policy is defined.

### Example: Configure Multiple Commands

```yaml
policies:
  slash_commands:
    /help:
      teams: ["all-staff"]
    /migrate:
      teams: ["release-engineering"]
      users: ["chaserx", "migration-bot"]
    /rename-destination:
      teams: ["release-engineering", "dev-ops"]
    /rewire-pipeline:
      teams: ["dev-ops"]
      users: ["pipeline-admin"]
    /add-team:
      teams: ["org-admins"]
```

Each command has its own access list. Commands not listed here are unavailable when any slash command policy is defined.

## Policy Precedence

When both issue policies and slash command policies are defined, Warp evaluates them in order:

1. **Issue policies** are evaluated first based on the issue's labels.
2. **Slash command policies** are evaluated second based on the command name.
3. **Access is granted** if either policy allows the user.

This means a user who is permitted by an issue policy can run a command even if they are not listed in the slash command policy for that command, and vice versa.

## Important Notes

* **Policy identifiers must be unique.** Each issue policy needs a distinct key (e.g., `onboarding`, `global_access`). Duplicate keys will cause one to overwrite the other.
* **Team slugs and usernames are case-sensitive.** Make sure they exactly match the GitHub team slug and username. For example, `Release-Engineering` is not the same as `release-engineering`.
* **Defining any policy activates restriction.** Adding even one issue policy means all issues are subject to policy checks. Adding even one slash command policy means all commands default to denied unless explicitly allowed.

## Complete Example

Here is a full `warp.yml` demonstrating both issue and slash command policies:

```yaml
version: "1.0"

policies:
  issues:
    # Global: release engineering can act on any issue
    release_team_access:
      teams: ["release-engineering"]
      users: ["sr-engineer"]

    # Label-specific: only the platform team can act on platform issues
    platform_team:
      labels: ["ado:team:platform", "ado:team:infrastructure"]
      teams: ["platform-engineering"]
      users: ["team-lead"]

    # Label-specific: sensitive operations require senior approval
    sensitive_ops:
      labels: ["production", "critical"]
      teams: ["senior-engineers"]
      users: ["vp-engineering"]

  slash_commands:
    /help:
      teams: ["all-contributors"]
    /migrate:
      teams: ["release-engineering", "dev-ops"]
      users: ["migration-specialist"]
    /rename-destination:
      teams: ["release-engineering"]
    /add-team:
      users: ["org-admin"]
```
