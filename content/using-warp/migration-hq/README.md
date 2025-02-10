---
icon: github
description: Learn How Warp Organizes your Migration Processes
---

# Migration HQ

<figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption><p>The <em>Migration HQ</em> page.</p></figcaption></figure>

The _Migration HQ_ repository — the _HQ_ is short for “headquarters” — is Warp’s primary user interface. When you create a Project, Warp generates this repository to be the “control panel” that you use to manage the migration process.

You will use the _Issues_ page of _Migration HQ_ most often. Warp uses this page for the list of migrations. For each repository that Warp finds in the sources you provide (e.g. Azure DevOps), it creates an issue representing that repository. Each issue acts as the user interface for managing the migration of its repository. You enter Warp commands in the issue’s _Comments_ section, including the command to migrate the issue from the source to GitHub.

You also might these _Migration HQ_ pages on occasion:

* **Actions:** Warp uses GitHub Actions to perform migrations and other tasks. You can see these Action in operations and find out if they’ve completed by visiting the _Actions_ page in _Migrations HQ_.
* **Code:** Warp uses _Migration HQ_’s _Code_ section to store configuration files, including:
  * config/v`ault.age`:  “The vault,” a file that stores the encrypted tokens that allow Warp to access the source and destination organizations.
  * `config/warp.yml`:  Warp’s main configuration file, which you can customize for more complex migration actions, such as rewiring Azure DevOps pipelines to point at GitHub.

