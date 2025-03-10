---
icon: objects-column
description: Provides a high-level overview of the migration Project.
---

# Dashboard

<figure><img src="../../.gitbook/assets/dashboard.png" alt=""><figcaption><p>Warp’s <em>Dashboard</em> page.</p></figcaption></figure>

The _Dashboard_ page provides a high-level overview of the Project’s size and progress. It also provides a link to the Project’s _Migration HQ_ repository.

The key parts of the _Dashboard_ page are described in detail below.

### Migration HQ

<figure><img src="../../.gitbook/assets/migration_hq_button.png" alt="" width="180"><figcaption></figcaption></figure>

The **Migration HQ** button takes you to the _Migration HQ_ repository for this Project. This repository acts as the control panel for the migration process.

### Trends

<figure><img src="../../.gitbook/assets/trends.jpg" alt=""><figcaption></figcaption></figure>

The _Trends_ section provides the following quantitative information about your Project:

* **Repositories Discovered:** The number of repositories that Warp was able to find after scanning the Azure DevOps organization(s) whose repositories you want to migrate. This display shows the total number of repositories that Warp found, followed by the number that were found in the past 24 hours.
* **Repositories Migrated:** The number of repositories that were migrated to GitHub. This display shows the total number of repositories that were migrated, followed by the number that were migrated in the past 24 hours.
* **Daily Average:** The average number of migrations performed per day since the Project’s first migration. This display shows the average (mean) migrations per day since the first one, followed by the number of days since the first migration.
* **Overall Progress:** The percentage of discovered repositories that have been migrated. This displays shows that percentage, followed by the percentage of discovered repositories yet to be migrated.

### By Source

<figure><img src="../../.gitbook/assets/by source.jpg" alt="" width="188"><figcaption></figcaption></figure>

The _By Source_ section lists the sources — that is, the organizations that you’re migrating repositories _from_.

For each source, this section shows the following:

* **Name:** The name of the organization.
* **Repositories Discovered:** The number of repositories discovered in this particular organization.
* **Repositories Migrated:** The number of repositories that were migrated from this particular organization to GitHub.
