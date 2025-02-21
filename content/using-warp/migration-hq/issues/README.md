---
icon: list-check
description: Where Warp stores its list of migrations
---

# Issues

The _Issues_ page of _Migration HQ_ is the list of the Project’s migrations. For each repository that Warp finds in the sources you provide (e.g. Azure DevOps), it creates an issue representing that repository:

<figure><img src="../../../.gitbook/assets/Every repository has its own issue (1).png" alt="&#x22;Every repository has its own issue&#x22; — diagram showing that for every repository in the source, Warp creates a corresponding issue in Migration HQ."><figcaption></figcaption></figure>

### Viewing Open Issues

**When you open&#x20;**_**Migration HQ**_**’s&#x20;**_**Issues**_**&#x20;page, you will see the open issues list, which GitHub displays by default.** Items in the open issues list correspond to repositories that have not yet been migrated:

<figure><img src="../../../.gitbook/assets/image (40).png" alt="The open issues list in the &#x22;Issues&#x22; page in Migration HQ."><figcaption><p>The <strong>open issues list</strong> in the <em>Issues</em> page, which displays the Project repositories that have not been migrated.</p></figcaption></figure>

**To view an open issue, click its name.** You will be taken to its issue page, which will display its details, and which you can use to issue commands, including the command to start a migration.

You can filter _Migration HQ_ issues in the same ways you would in a standard GitHub repository: by open/closed status, author, label, and so on.

### Viewing Closed Issues

Items in the closed issues list correspond to repositories that have either been migrated or ignored:

<figure><img src="../../../.gitbook/assets/image (42).png" alt="The closed issues list in the &#x22;Issues&#x22; page in Migration HQ."><figcaption><p>The <strong>closed issues list</strong> in the <em>Issues</em> page, which displays the Project’s migrated and ignored repositories.</p></figcaption></figure>

**To view an closed issue, click its name.** You will be taken to its issue page, which will display its details, including information about the migration.

### Closing Issues

There are two ways to close an open issue in _Migration HQ:_

1.  **Automatically.** After a successful migration of a repository to GitHub, Warp changes the status of its corresponding issue to _Closed_. The issue will move from the open issues list to the closed issues list, and the _Closed_ indicator will appear below the title of its page:\


    <figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1).png" alt="The top-level heading for an issue: &#x22;[Azure DevOps] TailwindTraders-Website&#x22;. The &#x22;Closed&#x22; indicator appears below the headline." width="375"><figcaption></figcaption></figure>
2.  **Manually.** You can close one or more issues manually by checking their boxes in the open issues list and selecting either **Completed** or **Not Planned** from the **Mark as** menu:\


    <figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt="The open issues list in the “Issues” page of Migration HQ. One of the issues is checked, and the user has the “Mark as” dropdown menu open and is selecting the “Completed” option."><figcaption><p>Marking an issue as <em>Completed</em>, which will cause the repository to be ignored.</p></figcaption></figure>

    You can also manually close an issue on its own page — see [_Issue Page_](issue-page.md) for details.\
    \
    **By closing an issue manually, you are choosing to&#x20;**_**ignore**_**&#x20;the repository.** Ignoring a repository has these effects:

* It moves the issue to the closed issues list.
* Warp will ignore any slash commands (commands that you issue to Warp) entered into the issue’s comments and it will not update the issue’s content.

### Re-opening Issues

If you decided that you need to re-migrate a repository, you can do so by re-opening its issue. You can re-open one or more issues by checking their boxes in the closed issues list and selecting **Open** from the **Mark as** menu:

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1).png" alt="The closed issues list in the “Issues” page of Migration HQ. One of the issues is checked, and the user has the “Mark as” dropdown menu open and is selecting the “Open” option."><figcaption><p>Marking an issue as <em>Open</em>, which makes it a candidate for migration again.</p></figcaption></figure>

Re-opening an issue has these effects:

* It moves the issue to the open issues list.
* Warp will once again pay attention to slash commands entered into the issue’s comments and will update the issue’s content as its status changes.

