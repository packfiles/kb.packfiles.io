---
description: Warp’s configuration file.
icon: file-check
---

# Warp.yml

Warp’s configuration file, `warp.yml`, is located in _Migration HQ_’s `config` directory. Its default version is almost entirely commented out, with the exception of its version number:

```yaml
# Welcome to your Warp configuration file!

# To learn more about the use and purpose of this file,
# refer to our documentation at https://pack.fm/about-warp-yml

version: "1.0"

####
# Repository Visibility
####
# Controls the visibility of repositories created by Warp during migration.
#
# Options:
#   - "private" (default): Repositories are only visible to users with explicit access
#   - "internal": Repositories are visible to all members of your GitHub organization
#
# Note: This setting only affects NEW repositories created by Warp. It does not
# modify the visibility of existing repositories.
#
# Uncomment target_repo_visibility and set to "internal" to make migrated repositories visible to
# your entire GitHub organization:
#
# target_repo_visibility: "internal"

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

For simple migrations, you probably won’t need to make any changes to `warp.yml`. However, with migrations that go beyond just moving code repositories from the source to the destination, you’ll find `warp.yml` useful for specifying additional details. For example, you can configure the visibility of migrated repositories or provide service connection IDs for Azure Pipelines rewiring.

## Repository Visibility

By default, Warp creates migrated repositories as **private**. If your organization uses GitHub Enterprise and you’d like migrated repositories to be visible to all organization members, you can set the `target_repo_visibility` option to `"internal"`.

```yaml
version: "1.0"
target_repo_visibility: "internal"
```

The `target_repo_visibility` field accepts two values:

* `"private"` (default) — only users with explicit access can see the repository
* `"internal"` — all members of your GitHub organization can see the repository

If the field is omitted or set to `"private"`, Warp uses its default behavior and creates private repositories.

{% hint style="info" %}
The `"internal"` visibility option requires a GitHub organization that supports internal repositories, such as [GitHub Enterprise Cloud](https://docs.github.com/en/enterprise-cloud@latest/admin/overview/about-github-enterprise-cloud) or GitHub Enterprise Server. This setting only affects **new** repositories created by Warp — it does not change the visibility of repositories that have already been migrated.
{% endhint %}
