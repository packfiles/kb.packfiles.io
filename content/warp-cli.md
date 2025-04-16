---
icon: square-terminal
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# Warp CLI

The Warp CLI gives you access to certain features of Warp directly from your terminal. In particular, it allows you to [work with the credentials you've stored in Warp Vault from the command line](using-warp/warp-vault/using-credentials-in-scripts/).&#x20;

Before you can use Warp CLI, you must have the [GitHub CLI](https://cli.github.com/) installed on your machine.

### Install the GitHub CLI

First, see if the GitHub CLI is installed on your computer.

Open your terminal application (on Windows, it’s _Windows PowerShell_ or _Command Prompt_; on macOS and Linux, the default terminal is named _Terminal_).

Enter the following command:

```bash
gh --version
```

If the GitHub CLI is installed, you’ll see a message showing its version number and the URL for its release notes. Here’s an example:

```bash
gh version 2.63.1 (2024-12-03)
https://github.com/cli/cli/releases/tag/v2.63.1
```

If you see an error message instead, you’ll need to install the GitHub CLI. Go to the [GitHub CLI page](https://cli.github.com/) and follow the instructions there.

### Install the Warp CLI Extension

Once you’ve confirmed that the GitHub CLI is installed on your computer, enter the following command to install the Warp command-line extension:

```bash
gh extension install packfiles/gh-warp
```

Confirm that the Warp command-line extension is installed by running the following command in a terminal window:

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
```
