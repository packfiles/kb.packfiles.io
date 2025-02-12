---
icon: ufo
description: GitHub Codespaces...but with Warp!
---

# Warpspaces

### Overview

Before we talk about Warpspaces, let’s review GitHub Codespaces. A Codespace is a fully configured development environment that runs in the cloud, accessible via a web browser or VS Code, and hosted by GitHub. Every Codespace comes with common tools such as git, Python, Node.js, and other programming languages pre-installed. Codespaces can also be customized with other packages.

Warpspaces are Codespaces that have been customized with useful tools for performing migrations, including:

* GitHub’s CLI tools
* GitHub’s migration tools
* Warp’s CLI tools

With a Warpspace, you get a secure, controlled Codespace environment with all the tools you would need to manually run migration tools, perform a manual migration, or manage an edge case where Warp alone will not handle your migration.

### Opening a Warpspace

<figure><img src="../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

To open a Warpspace for a Project:

* Open the Project’s _Migration HQ_ repository,
* Click the **Code** button,
* Select the **Codespaces** tab, and
* Click the **+** button or, if it’s available, the **Create codespace on main** button.

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>The Warpspace during the initialization process.</p></figcaption></figure>

The Warpspace will take a couple of minutes to initialize, since it has to import a large set of packages. Once initialized, you’ll be in GitHub’s Codespace environment with a complete set of command-line migration tools and utilities:

<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption><p>The Warpspace after initialization.</p></figcaption></figure>
