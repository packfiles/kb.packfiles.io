---
description: Configuring Warp to use self-hosted runners
icon: file-check
---

# Runner Configuration

There are very few cases where you might need to change or update the `.github/workflows/runner.yml` file in the Migration HQ project.

One such case is when you are using [self-hosted runners](https://docs.github.com/en/actions/concepts/runners/self-hosted-runners).

## Self-hosted Runner Configuration Option

Update the `runs-on` value from `ubuntu-latest` to `self-hosted`. See GitHub's ["Choosing the runner for the job"](https://docs.github.com/en/actions/how-tos/write-workflows/choose-where-workflows-run/choose-the-runner-for-a-job) documentation for more info on self-hosted runners.

```yaml
# This Action is used by Packfiles Warp to perform migration-related tasks
# in your GitHub environment.
#
# Packfiles takes the security of your migration seriously, and we're
# committed to providing you with total visibility and granular control
# over how and where your data is processed.
#
# For more information about the Warp Runner Agent, refer to our
# documentation at https://pack.fm/about-warp-runner

name: Warp Runner Agent

permissions:
  contents: write
  actions: write
  issues: write
  pull-requests: write
  repository-projects: write

on:
  workflow_dispatch:
    inputs:
      boot:
        description: 'Boot Payload'
        required: true
        type: string

jobs:
  runner:
    name: "Packfiles Warp Runner Agent"
    runs-on: self-host # the default is ubuntu-latest
    continue-on-error: true

    steps:
      - uses: packfiles/runner-agent@v1
        with:
          boot-payload: ${{ inputs.boot }}
          migration-hq-vars: ${{ toJSON(vars) }}
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          PKFS_MASTER_KEY: ${{ secrets.PKFS_MASTER_KEY }}

# PKFS_RUNNER_WORKFLOW_VERSION=2025-01-26
```
