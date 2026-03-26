---
description: Warp’s configuration file.
icon: file-check
---

# Warp.yml

Warp’s configuration file, `warp.yml`, is located in _Migration HQ_’s `config` directory. Its default version is almost entirely commented out, with the exception of its version number:

```
# Welcome to your Warp configuration file!

# To learn more about the use and purpose of this file, 
# refer to our documentation at https://pack.fm/about-warp-yml

version: "1.0"

####
# Example - Azure Pipelines Rewiring
####
# To configure the service connection ID of the Azure Pipelines GitHub App,
# which is used to rewire Azure Pipelines to point at GitHub, apply the 
# configuration below.

# azure_devops:
#   global: # For a global default 
#     azure_pipelines_github_app_service_connection_id: <your Azure Pipelines GitHub App Service Connection ID>
#   my-org-name: # You can also supply organization-specific defaults
#     azure_pipelines_github_app_service_connection_id: <your Azure Pipelines GitHub App Service Connection ID>
```

For simple migrations, you probably won’t need to make any changes to `warp.yml`. However, with migrations that go beyond just moving code repositories from the source to the destination, you’ll find warp.yml useful for specifying additional details.

For example, if your migration process involves reconfiguring your Azure Pipelines to use GitHub repositories, you’ll need to make changes to the default `warp.yml` to provide additional required information, such as service connection IDs.

## Advanced Configuration

Beyond basic setup, `warp.yml` supports several advanced features that let you customize your migration workflows.

### Custom Scripts

Define custom automation scripts in your Migration HQ’s `bin/` directory and execute them from issue comments using the `/run` slash command. Warp supports Bash, PowerShell, Ruby, and Python scripts with configurable arguments and optional Vault access.

[Learn more about Custom Scripts](custom-scripts.md)

### Access Policies

Control who can execute slash commands and perform actions on backlog entry issues. Policies use an opt-in security model — when defined, only explicitly approved users and teams can perform the configured actions.

### Custom Tasks

Add reusable checklists and task content to issues based on labels. Custom tasks are automatically injected into or removed from issue descriptions when matching labels are added or removed.

### Target Repository Visibility

Control whether repositories created by Warp during migration are set to `private` (default) or `internal` visibility.
