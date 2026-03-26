---
description: Extend Warp with custom automation scripts.
icon: terminal
---

# Custom Scripts

Custom Scripts let you define automation scripts in your Migration HQ repository and execute them directly from issue comments using the [`/run`](../slash-commands/global/run.md) slash command. Use them to automate repetitive tasks, integrate with external systems, or extend your migration workflows.

**How it works:**

1. Write a script and place it in the `bin/` directory of your Migration HQ repository
2. Register the script in your `warp.yml` configuration file
3. Execute it from any backlog entry issue with `/run <script_id>`

Warp supports **Bash**, **PowerShell**, **Ruby**, and **Python** scripts.

## Prerequisites

Before using Custom Scripts, ensure you have:

* Admin access to your Migration HQ repository
* Scripts stored in the `bin/` directory at the root of Migration HQ
* Scripts marked as executable (`chmod +x bin/your_script.sh`)
* A valid `warp.yml` configuration in the `config/` directory

## Configuration

Define scripts in your `warp.yml` file under the `scripts:` key. Each script entry uses a unique identifier as its key.

### Required Fields

| Field | Type | Description |
| --- | --- | --- |
| `name` | String | Human-friendly name displayed in responses and help messages |
| `description` | String | Brief explanation of what the script does |
| `language` | String | Script language: `bash`, `pwsh`, `python`, or `ruby` |
| `filename` | String | Name of the script file in the `bin/` directory |

### Optional Fields

| Field | Type | Description |
| --- | --- | --- |
| `allow_vault` | Boolean | When `true`, injects `PKFS_MASTER_KEY` into the script's environment |
| `arguments` | Object | Named arguments the script accepts (see [Script Arguments](#script-arguments)) |

### Basic Example

```yaml
version: "1.0"

scripts:
  notify_team:
    name: "Notify Team"
    description: "Send a notification to the team channel"
    language: bash
    filename: "notify_team.sh"
    allow_vault: false
```

With the corresponding script at `bin/notify_team.sh`:

```bash
#!/bin/bash
set -e

echo "Notifying team about migration for ${WARP_BACKLOG_ENTRY_SOURCE}"
# Add your notification logic here
```

Execute it from an issue comment:

```
/run notify_team
```

## Script Arguments

Scripts can accept named arguments that are validated by Warp before execution.

### Defining Arguments

Add an `arguments` block to your script configuration. Each argument has a `description` (required) and an optional `required` flag.

```yaml
scripts:
  update_wiki:
    name: "Update Wiki"
    description: "Update the migration wiki page"
    language: ruby
    filename: "update_wiki.rb"
    allow_vault: false
    arguments:
      wiki_page:
        description: "The wiki page to update"
        required: true
      status:
        description: "Current migration status"
        required: true
      notify:
        description: "Send a notification after updating"
```

Arguments without `required: true` are optional.

### Passing Arguments at Runtime

Use the `--script_args` flag followed by space-separated `key=value` pairs:

```
/run update_wiki --script_args wiki_page=migrations status=in_progress
```

Boolean flags are also supported — they set the argument value to `"true"`:

```
/run update_wiki --script_args wiki_page=migrations status=in_progress notify
```

{% hint style="info" %}
Warp validates arguments before executing your script. Missing required arguments or unrecognized argument names will produce an error message — your script will not run.
{% endhint %}

### How Arguments Are Delivered

Arguments are passed to your script as environment variables with the prefix `WARP_SCRIPT_ARGS__`, followed by the argument name converted to uppercase with non-alphanumeric characters replaced by underscores.

**Examples:**

| Argument Name | Environment Variable |
| --- | --- |
| `wiki_page` | `WARP_SCRIPT_ARGS__WIKI_PAGE` |
| `tenant-id` | `WARP_SCRIPT_ARGS__TENANT_ID` |
| `db.url` | `WARP_SCRIPT_ARGS__DB_URL` |

## Environment Variables

Warp injects the following environment variables into every script execution:

| Variable | Description | Always Available |
| --- | --- | --- |
| `WARP_SCRIPT_ID` | The script's identifier from `warp.yml` | Yes |
| `WARP_SCRIPT_NAME` | The script's human-friendly name | Yes |
| `WARP_SCRIPT_DESCRIPTION` | The script's description | Yes |
| `WARP_SCRIPT_ARGS__<NAME>` | Value for each provided argument | Yes (one per argument) |
| `WARP_PROJECT_ID` | The Warp project ID | Yes |
| `WARP_BACKLOG_ENTRY_ID` | The backlog entry (issue) ID | Yes |
| `WARP_BACKLOG_ENTRY_DESTINATION` | The target repository name | Yes |
| `WARP_BACKLOG_ENTRY_SOURCE` | The source repository name | Yes |
| `PKFS_MASTER_KEY` | The Vault master key for decrypting credentials | Only when `allow_vault: true` |

## Vault Integration

When `allow_vault` is set to `true`, Warp injects the `PKFS_MASTER_KEY` environment variable into your script's execution environment. This allows your script to decrypt and query credentials stored in your Warp Vault.

```yaml
scripts:
  sync_repos:
    name: "Sync Repositories"
    description: "Sync repository settings using source credentials"
    language: bash
    filename: "sync_repos.sh"
    allow_vault: true
```

Your script can then use the Warp CLI to query vault credentials:

```bash
#!/bin/bash
set -e

export BBS_USERNAME=$(gh warp vault get '(type:bitbucketserver).credentials.username')
export BBS_PASSWORD=$(gh warp vault get '(type:bitbucketserver).credentials.password')

echo "Syncing with Bitbucket Server as ${BBS_USERNAME}"
# Add your sync logic here
```

{% hint style="warning" %}
Enabling `allow_vault` gives the script access to **all credentials** in your Vault. Only enable this for scripts that require credential access.
{% endhint %}

For details on the Vault query syntax, see [Using Credentials in Scripts](../warp-vault/using-credentials-in-scripts/).

## Script Examples by Language

### Bash

```bash
#!/bin/bash
set -e

repo_name="${WARP_BACKLOG_ENTRY_DESTINATION}"
source_name="${WARP_BACKLOG_ENTRY_SOURCE}"
gh_username="${WARP_SCRIPT_ARGS__GH_USERNAME}"

echo "Validating repository: ${repo_name} for user: ${gh_username}"
gh repo view "${gh_username}/${repo_name}" --json name,isPrivate,visibility
```

### PowerShell

```powershell
#!/usr/bin/env pwsh
param()

$RepoName = $env:WARP_BACKLOG_ENTRY_DESTINATION
$ReportType = $env:WARP_SCRIPT_ARGS__REPORT_TYPE
$OutputPath = $env:WARP_SCRIPT_ARGS__OUTPUT_PATH

Write-Host "Generating $ReportType report for $RepoName to $OutputPath"
# Add your report generation logic here
```

### Ruby

```ruby
#!/usr/bin/env ruby
require "bundler/inline"

gemfile do
  source "https://rubygems.org"
  gem "octokit"
end

require "octokit"

source_repo = ENV["WARP_BACKLOG_ENTRY_SOURCE"]
destination_repo = ENV["WARP_BACKLOG_ENTRY_DESTINATION"]
owner = ENV["WARP_SCRIPT_ARGS__OWNER"]

puts "Syncing labels from #{source_repo} to #{destination_repo} for #{owner}"
# Add your label sync logic here
```

### Python

```python
#!/usr/bin/env python3
import os
import sys

migration_id = os.getenv("WARP_BACKLOG_ENTRY_ID", "unknown")
metric_type = os.getenv("WARP_SCRIPT_ARGS__METRIC_TYPE", "commits")

print(f"Analyzing {metric_type} for migration: {migration_id}")
# Add your analysis logic here
```

## Access Control

Script execution can be restricted using policies in your `warp.yml`. Define a `policies.scripts` block to control who can run each script.

```yaml
policies:
  scripts:
    sync_repos:
      teams: ["release-engineering", "dev-ops"]
      users: ["migration-admin"]
```

When a script policy is defined, only the listed users and teams can execute that script. Users not on the list will see an error message listing who is authorized.

When no script policies are defined, all organization members can run all scripts.

## Execution

Custom scripts run on a GitHub Actions runner agent within your Migration HQ repository. When a script completes, Warp automatically posts a comment on the issue:

* **On success:** A confirmation message with a link to the workflow run
* **On failure:** An error message with the exit code and a link to the workflow run logs

You can view detailed logs by navigating to the **Actions** tab of your Migration HQ repository and selecting the workflow run. For more information on viewing runner logs, see [Runner Agent](runner-agent.md).

## Running a Script

To execute a custom script, post a comment on a backlog entry issue using the [`/run`](../slash-commands/global/run.md) slash command:

```
/run <script_id> [--script_args key=value ...]
```

See the [`/run` command reference](../slash-commands/global/run.md) for full usage details.

## Best Practices

1. **Add shebang lines** — Always include `#!/bin/bash`, `#!/usr/bin/env ruby`, etc. at the top of your scripts
2. **Make scripts executable** — Run `chmod +x bin/your_script.sh` before committing
3. **Validate inputs** — Check for required data and provide helpful error messages
4. **Use descriptive names** — Choose clear script identifiers and file names
5. **Document arguments** — Write clear descriptions for each argument in `warp.yml`
6. **Handle errors gracefully** — Use proper exit codes (`set -e` in Bash) and error handling
7. **Test locally first** — Verify scripts work before adding them to `warp.yml`
8. **Keep scripts focused** — Each script should do one thing well

## Troubleshooting

| Issue | Solution |
| --- | --- |
| Script not found | Verify the `filename` in `warp.yml` matches the actual file in `bin/` |
| Permission denied | Make the script executable: `chmod +x bin/your_script.sh` and commit |
| Arguments not working | Use `--script_args key=value` format. Check that argument names match the `arguments` block in `warp.yml` |
| Script fails silently | Add error handling and logging to your script. Use `set -e` in Bash scripts |
| Unauthorized | Check `policies.scripts` in `warp.yml` and verify your username or team membership |
| Script not available | Ensure `warp.yml` has been committed and pushed to your Migration HQ's default branch |
