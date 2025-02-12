---
icon: '6'
---

# Migrate a Repository

So far, here’s what you’ve done:

* Created a new Project
* Generated personal access tokens for Azure DevOps and GitHub
* Set up the vault
* Stored the vault key in _Migration HQ_
* Connected your Azure DevOps account to Warp
* Scanned the Azure DevOps Organization for repositories.

It’s finally time to migrate a repository from Azure DevOps to GitHub!

{% include "../../.gitbook/includes/search-for-the-emoji-if....md" %}



🛠️ Switch to the browser tab or window with _Migration HQ_ and select the **Issues** tab:

![The Issues page for the Migration HQ repository.](../../media/images/quickstart/migrate/github_issues.png)

Warp creates an issue in the _Migration HQ_ repository for every repository it finds in your Azure DevOps organization. These issues are used to manage the migration of repositories from Azure DevOps to GitHub.

🛠️ Click on the issue for the repository you want to migrate. In this example, we’re clicking on the issue named **TailwindTraders-Website**.

The page for the issue will appear:

<figure><img src="../../media/images/quickstart/migrate/github_issue_1.png" alt=""><figcaption><p>The issue page for one of the repositories to be migrated.</p></figcaption></figure>

The body of the issue — the part that contains a description and other notes about the issue — contains information assembled by Warp about the corresponding repository.

If you take a closer look at the body, you’ll see that it’s divided into the following subsections:

* **Migration Status:** This section shows the current status of the migration. Since the migration hasn’t started yet, its status is **not started**.

<figure><img src="../../media/images/quickstart/migrate/github_issue_2.png" alt=""><figcaption><p>The top part of the issue’s body.</p></figcaption></figure>

* **Tasks:** This section has a checklist of the tasks that need to be performed to migrate the repository. Warp will automatically check off the tasks as they are completed.

<figure><img src="../../media/images/quickstart/migrate/github_issue_3.png" alt=""><figcaption><p>The bottom part of the issue’s body.</p></figcaption></figure>

* **About:** This lists basic information about the source repository, such as when its last commit was, how many commits it’s had in the past year, who its most active contributor was, and its size.
* **Source & Destination:** This provides links to the source and the destination repositories.
* **Inventory:** This shows information about the destination repository. Since the migration hasn’t started yet, this section simply says that the repository hasn”t been migrated yet.

<figure><img src="../../media/images/quickstart/migrate/github_issue_4.png" alt=""><figcaption><p>The comments section of the issue.</p></figcaption></figure>

It’s time to migrate!

🛠️ Scroll down the page to the comments section...

<figure><img src="../../media/images/quickstart/migrate/github_issue_start_migration.png" alt=""><figcaption><p>Issuing the <code>/migrate</code> command.</p></figcaption></figure>

🛠️ ...and in the first comment, enter the following command:

```bash
/migrate
```

In moments, Warp will reply with a follow-up comment announcing that the migration has started:

<figure><img src="../../media/images/quickstart/migrate/github_issue_migration_in_process_comment.png" alt=""><figcaption><p>Warp’s response comment to the <code>/migrate</code> command.</p></figcaption></figure>

Depending on a number of factors, including the size of the repository and how many migrations Warp is performing at the same time, the migration may take a few to several minutes to complete.

🛠️ In the meantime, switch to the browser tab or windows for _Migration HQ_ and click the **Actions** tab:

<figure><img src="../../media/images/quickstart/migrate/actions_tab_1.png" alt=""><figcaption><p>The <em>Actions</em> page of <em>Migration HQ</em>, showing the runner agent performing the migration. </p></figcaption></figure>

You should see a new workflow with a spinning yellow icon named **Warp Runner Agent**. The yellow icon denotes that it is currently running. This workflow is performing the task of migrating the repository from Azure DevOps to GitHub.

<figure><img src="../../media/images/quickstart/migrate/actions_tab_2.png" alt=""><figcaption><p>The <em>Actions</em> page of <em>Migration HQ</em>, after the runner agent has completed its tasks.</p></figcaption></figure>

Eventually, the runner agent will complete its tasks, and its icon will change from spinning yellow to a green circle with a checkmark. This means that Warp has finished migrating the repository.

🛠️ Confirm that the repository has been migrated by clicking the **Issues** tab:

<figure><img src="../../media/images/quickstart/migrate/post-migration_open_issues.png" alt=""><figcaption><p>The open issues tab of the <em>Issues</em> page in <em>Migration HQ</em>. Note that there is one less open issue.</p></figcaption></figure>

You’ll see the list of open issues. In our example, there are now only _four_ open issues, where there were _five_ originally. Migrating the repository closed its issue.

🛠️ Let’s look at the closed issues. Click on the **Closed** tab.

You’ll see the list of closed issues. It should contain the issue for the repository you just migrated:

<figure><img src="../../media/images/quickstart/migrate/post-migration_closed_issues.png" alt=""><figcaption><p>The closed issues tab of the <em>Issues</em> page in <em>Migration HQ</em>. Note that there is one new closed issue.</p></figcaption></figure>

🛠️ Examine the issue by clicking it:

<figure><img src="../../media/images/quickstart/migrate/closed_issue_1.png" alt=""><figcaption><p>The closed issue’s updated <em>Migration Status</em> section.</p></figcaption></figure>

When the issue page opens, you’ll see a number of changes:

* The **Migration Status** section now shows a graphic indicating that the migration is complete.
* The _Migrate this repository’s comments to GitHub_ checkbox in the **Tasks** list is now checked.

<figure><img src="../../media/images/quickstart/migrate/closed_issue_2.png" alt=""><figcaption><p>The closed issue’s updated <em>Source &#x26; Destination</em> and <em>Inventory</em> sections.</p></figcaption></figure>

* The **Source and Destination** section now has links for both the source and destination repositories.
* The **Inventory** section now shows information about the migrated repository.

🛠️ Scroll to the comments section:

<figure><img src="../../media/images/quickstart/migrate/closed_issue_3.png" alt=""><figcaption><p>The closed issue’s comments section, featuring Warp’s comment saying that the migration was successful.</p></figcaption></figure>

You’ll see a new comment from Warp, complete with a link to the destination repository.

🛠️ Click on the link to visit the newly-migrated repository.

You’ll see the repository’s page — _in GitHub!_ — with all of its files, branches, and commits:

<figure><img src="../../media/images/quickstart/migrate/migrated_repo.png" alt=""><figcaption><p>The newly migrated repository in GitHub.</p></figcaption></figure>

When you started, the GitHub organization had a single repository: _Migration HQ_.

🛠️ Click on the organization’s name (near the top left corner of the page), followed by the **Repositories** tab.

![The GitHub organization’s Repositories page, showing Migration HQ and the newly migrated repository.](../../media/images/quickstart/migrate/github_organization_repos.png)

You’ll see that the organization now has _two_ repositories: _Migration HQ_ and the repository you just migrated from Azure DevOps.

{% hint style="success" %}
🙌 Congratulations!🙌&#x20;

&#x20;You’ve successfully migrated a repository from Azure DevOps to GitHub using Warp.
{% endhint %}
