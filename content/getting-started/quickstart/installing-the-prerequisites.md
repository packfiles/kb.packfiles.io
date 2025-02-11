---
description: How to install the requires applications on your local computer.
---

# Installing the Prerequisites

### Overview

Before you can use Warp, you must have the following applications installed on your local computer:

1. **GitHub CLI**. Warp uses an extension to the GitHub command-line interface to send key credentials data to your _Migration HQ_ repository in GitHub.
2. **The Warp command-line extension.** This utility assembles the secure vault file containing tokens authorizing access to your source and destination repositories, generates the key to unlock the vault file, and puts both in your _Migration HQ_ repository.

{% include "../../.gitbook/includes/search-for-the-emoji-if....md" %}

### Installing the GitHub CLI

First, see if the GitHub CLI is installed on your computer.

🛠️ Open your terminal application (on Windows, it’s _Windows PowerShell_ or _Command Prompt_; on macOS and Linux, the default terminal is named _Terminal_).

🛠️ Enter the following command:

```bash
gh --version
```

If the GitHub CLI is installed, you’ll see a message showing its version number and the URL for its release notes. Here’s an example:

```bash
gh version 2.63.1 (2024-12-03)
https://github.com/cli/cli/releases/tag/v2.63.1
```

If you see an error message instead, you’ll need to install the GitHub CLI. Go to the [GitHub CLI page](https://cli.github.com/) and follow the instructions there.

### Installing the Warp Command-Line Extension

🛠️ Once you’ve confirmed that the GitHub CLI is installed on your computer, enter the following command to install the Warp command-line extension:

```bash
gh extension install packfiles/gh-warp
```

🛠️ Confirm that the Warp command-line extension is installed by running the following command in a terminal window:

```bash
gh warp
```

You should see this response:

```
      _ _ _                  
     | | | |___ ___ ___      
     | | | | .'|  _| . |     
     |_____|__,|_| |  _|     
Gets You To GitHub |_| vx.x.x
   With ❤️ From Packfiles.io 
                             
You're running the latest version of gh-warp (vx.x.x)
                                                     
GitHub migration superpowers, at your fingertips.

Usage:
  warp [command]

Available Commands:
  completion  Generate the autocompletion script for the specified shell
  help        Help about any command
  vault       Configure a Project Repository's credential vault

Flags:v
  -h, --help      help for warp
  -v, --version   version for warp

Use "warp [command] --help" for more information about a command.
```

{% hint style="success" %}
If you’ve made it this far, congratulations!

You’ve successfully installed the prerequisites for Warp. 🙌
{% endhint %}
