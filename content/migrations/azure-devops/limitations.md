---
description: Learn about Limitations for Data Migrated from Azure DevOps Services
icon: weight-scale
---

# Limitations

Although we strive to increase the fidelity and richness of Warp's migration capabilities, there are some limitations to the types of data that can be migrated under certain conditions.

#### Size Limitations

* No single Git commit can exceed **2 gigabytes** in size.
* Git references may not exceed **255 bytes** in size.
* No single file in the source repository can exceed **400 megabytes** in size.
* The absolute size limit for an individual repository is **40 gigabytes**.
* The size limit for metadata associated with a repository (including issues, pull requests, releases, and attachments) is **20 gigabytes**.
* Migrating **Git LFS** objects is currently unsupported, but on our roadmap.

To assist you in identifying and remediating repositories that exceed these size limits, Warp will automatically assign a "**too-big**" label to their Backlog Issue.&#x20;

