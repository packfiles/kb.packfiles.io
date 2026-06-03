---
description: Get Help Anytime with Warp's GitHub Copilot Agent
icon: robot
---

# Packfiles GitHub Copilot Agent

**The *Packfiles GitHub Copilot Agent* is an AI agent built into the Packfiles Warp app that helps you plan, execute, and troubleshoot migrations without leaving GitHub.**

Instead of consulting documentation, manually reviewing repository inventories, or reading runner logs to decode a failure, you can work directly with the agent in the places where migration work already happens: the *Migration HQ* Agents tab, a backlog issue, or a pull request.

## Prerequisites

Before using the *Packfiles GitHub Copilot Agent*, **ensure that**:

* Your *Migration HQ* repository has been initialized by Warp and a source scan has completed successfully, so that backlog issues have been created for your repositories
* GitHub Copilot is enabled for your organization
* Packfiles Warp App is installed on your Migration HQ organization
* You complete the setup steps outlined below to give the agent the necessary permissions to operate in your Migration HQ repository

### Setup
To configure the agent for your Migration HQ repository:

1. Add the following GitHub MCP configuration under `Migration-HQ → Settings → Code & automation → Copilot → Coding agent`:

	```json
	{
		"mcpServers": {
				"github-mcp-server": {
				"type": "http",
				"url": "https://api.githubcopilot.com/mcp",
				"tools": ["*"],
				"headers": {
					"X-MCP-Toolsets": "issues,pull_requests,repos,actions"
				}
			}
		}
	}
	```
	Ensure you've saved the configuration before proceeding to the next step.
2. Create a fine-grained PAT with: 
	* **Issues**: read+write
	* **Pull requests**: read+write 

	on the `Migration-HQ` repository only.
3. Add the PAT as a secret named `COPILOT_MCP_GITHUB_PERSONAL_ACCESS_TOKEN` in the `Migration-HQ` repository under `Settings → Secrets and variables → Agents`.
4. Follow the instructions in the [GitHub documentation](https://docs.github.com/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-agents/enable-copilot-cloud-agent#enabling-agent-apps-and-third-party-agents) to enable agent apps at the Enterprise level.

This setup allows the agent to make diagnostic comments on backlog issues and pull requests, and to create new wave labels for migration planning. For more information on the agent's capabilities and how to invoke them, see the next section.

## What the Agent Can Do

The *Packfiles GitHub Copilot Agent* has three capabilities, each invoked from a different entry point in *Migration HQ*:

| Capability | Where to invoke it | What it does |
|---|---|---|
| [**Migration Planning**](./migration-planning.md) | Agents tab | Reads your backlog issues, scores every repository, assigns migration waves, applies wave labels, and produces a complete migration strategy document |
| [**Migration Diagnosis**](./migration-diagnosis.md) | Assign a failed backlog issue to the agent | Identifies the root cause of a failure and posts a remediation plan |
| [**Validate Configuration**](./validate-configuration.md) | Pull request comment | Reads a `config/warp.yml` diff, validates the configuration against Warp's schema, and posts a structured findings report |

The agent supports both **Azure DevOps** and **Bitbucket Server** migrations, including projects with a mix of both sources.

## Further Reading

* [Migration Planning](./migration-planning.md) — Plan your migration waves and generate a strategy document
* [Migration Diagnosis](./migration-diagnosis.md) — Diagnose and fix failed migrations
* [Validate Configuration](./validate-configuration.md) — Validate and author `config/warp.yml` changes