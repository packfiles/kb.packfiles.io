---
icon: github
description: Learn How Warp Organizes your Migration Processes
---

# Migration HQ

<figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption><p>The <em>Migration HQ</em> page.</p></figcaption></figure>

**The&#x20;**_**Migration HQ**_**&#x20;repository — the&#x20;**_**HQ**_**&#x20;is short for “headquarters” — is Warp’s primary user interface.** When you create a Project, Warp generates a _Migration HQ_ repository for that project; it’s the “control panel” that you use to manage the migration process.

**You will use the** [_**Issues**_](issues/) **page of&#x20;**_**Migration HQ**_**&#x20;most often.** Warp uses this page for the list of migrations. For each repository that Warp finds in the sources you provide (e.g. Azure DevOps), it creates an issue representing that repository. Each issue acts as the user interface for managing the migration of its repository. You enter Warp commands in the issue’s _Comments_ section, including the command to migrate the issue from the source to GitHub.

You also might these _Migration HQ_ pages on occasion:

* **Actions:** Warp uses GitHub Actions to perform migrations and other tasks. You can see these Action in operations and find out if they’ve completed by visiting the _Actions_ page in _Migrations HQ_.
* **Code:** Warp uses _Migration HQ_’s _Code_ section to store configuration files, including:
  * config/v`ault.age`:  “The vault,” a file that stores the encrypted tokens that allow Warp to access the source and destination organizations.
  * `config/warp.yml`:  Warp’s main configuration file, which you can customize for more complex migration actions, such as rewiring Azure DevOps pipelines to point at GitHub.

