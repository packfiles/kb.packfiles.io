---
description: Validate and review config/warp.yml changes in pull requests
---

# Validate Configuration (config/warp.yml)

**The *Validate Configuration* skill reads your `config/warp.yml`, validates it against Warp's configuration schema, and posts a structured findings report so you can merge configuration changes with confidence.**

Warp's configuration file supports a range of settings: repository visibility, Azure Pipelines rewiring, access policies, custom task checklists, and scripts. As configurations grow more complex, it becomes easy to introduce errors that only surface at runtime. The agent catches those issues before they do.

## How to Use It

1. Open a pull request that modifies `config/warp.yml`. 
2. Post a comment on the pull request mentioning the **Packfiles Warp** agent and ask it to *"validate the configuration."*

#### Example:

> *"@packfiles-warp Can you validate the config changes in this PR?"*

The agent reads the current contents of `config/warp.yml` from the pull request's branch, validates it, and posts a review comment on the pull request with its findings.

## Finding Severity Levels

Each finding in the report is assigned one of three severity levels:

* **✅ Valid** — the configuration is correct and there are no concerns
* **⚠️ Warning** — the configuration is syntactically valid, but has implications worth reviewing before merging
* **❌ Error** — the configuration is incorrect or will prevent Warp from working as intended; must be fixed before merging

## Security Checks

Beyond schema validation, the agent flags configuration changes that could have security implications.

These are surfaced as warnings rather than errors, since they may be intentional. The report explains the implication so you can make an informed decision before merging.

## Further Reading

* [Warp.yml](../warp.yml.md) — Full configuration reference
* [Access Policies](../access-policies.md) — How to configure slash command and issue policies
* [Custom Tasks](../custom-tasks.md) — How to define label-triggered checklists
* [Custom Scripts](../custom-scripts.md) — How to register and run automation scripts