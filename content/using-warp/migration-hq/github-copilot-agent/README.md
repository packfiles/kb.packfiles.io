---
description: Get Help Anytime with Warp's GitHub Copilot Agent
icon: robot
---

# Warp GitHub Copilot Agent

**The *Warp GitHub Copilot Agent* is an AI agent built into the Packfiles Warp app that helps you plan, execute, and troubleshoot migrations without leaving GitHub.**

Instead of consulting documentation, manually reviewing repository inventories, or reading runner logs to decode a failure, you can work directly with the agent in the places where migration work already happens: the *Migration HQ* Agents tab, a backlog issue, or a pull request.

## What the Agent Can Do

The *Warp GitHub Copilot Agent* has three capabilities, each invoked from a different entry point in *Migration HQ*:

| Capability | Where to invoke it | What it does |
|---|---|---|
| [**Migration Planning**](./migration-planning.md) | Agents tab | Reads your backlog issues, scores every repository, assigns migration waves, applies wave labels, and produces a complete migration strategy document |
| [**Migration Diagnosis**](./migration-diagnosis.md) | Assign a failed backlog issue to the agent | Identifies the root cause of a failure and posts a remediation plan |
| [**Validate Configuration**](./validate-configuration.md) | Pull request comment | Reads a `config/warp.yml` diff, validates the configuration against Warp's schema, and posts a structured findings report |

The agent supports both **Azure DevOps** and **Bitbucket Server** migrations, including projects with a mix of both sources.

## Prerequisites

Before using the *Warp GitHub Copilot Agent*, ensure that:

* Your *Migration HQ* repository has been initialized by Warp and a source scan has completed successfully, so that backlog issues have been created for your repositories
* GitHub Copilot is enabled for your organization
* Packfiles Warp App is installed on your Migration HQ organization

## Further Reading

* [Migration Planning](./migration-planning.md) — Plan your migration waves and generate a strategy document
* [Migration Diagnosis](./migration-diagnosis.md) — Diagnose and fix failed migrations
* [Validate Configuration](./validate-configuration.md) — Validate and author `config/warp.yml` changes