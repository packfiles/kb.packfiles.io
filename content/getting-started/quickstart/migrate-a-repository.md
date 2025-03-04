---
icon: '6'
description: Let’s migrate!
---

# Migrate a Repository

### Objective

At last, it’s time to migrate a repository to GitHub! You’ll do this entirely in _Migration HQ_.

**At the end of this section, you will have a repository that has been migrated from its source and into your GitHub organization.**

{% include "../../.gitbook/includes/search-for-the-emoji-if....md" %}

### Select a Repository to Migrate

After scanning your source for repositories, you navigated to _Migration HQ_’s _Issues_ page, where you saw the open issues list:

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt="Migration HQ’s Issues page, with a close-up view of the open issues list."><figcaption><p><em>Migration HQ</em>’s <em>Issues</em> page, with a close-up view of the open issues list.</p></figcaption></figure>

Each item in the open issues list represents a repository to be migrated. After migrating a repository, Warp automatically closes its issue, which moves it to the closed issues list.

Let’s migrate a repository! For this example, we’ll migrate **TailwindTraders-Website**, whose issue is at the top of the open issues list pictured above.

🛠️ In your open issues list, click on the issue for the repository you want to migrate.

The page for the issue will appear:

<figure><img src="../../.gitbook/assets/image (2).png" alt="The page for the TailwindTraders-Website issue."><figcaption><p>The page for the <em>TailwindTraders-Website</em> issue.</p></figcaption></figure>

### Migrate the Repository

🛠️ Scroll to the comments section at the bottom of the issue page:

<figure><img src="../../.gitbook/assets/image (15).png" alt="The &#x22;Add a comment&#x22; box at the bottom of the page for the &#x22;TailwindTraders-Website&#x22; issue."><figcaption><p>The <em>Add a comment</em> box at the bottom of the page for the <em>TailwindTraders-Website</em> issue.</p></figcaption></figure>

You issue commands to Warp in comments by using _slash commands_ — commands that begin with the slash (`/`) character. One of these commands is /migrate, which tells Warp to migrate the repository represented by this issue.

🛠️ Enter the slash command `/migrate` into the comment box and click the **Comment** button.

A couple of seconds later, Warp will confirm that it received the command. The comments section will look like this:

<figure><img src="../../.gitbook/assets/image (16).png" alt="The comments section of the page for the TailwindTraders-Website issue. The first comment, by the user “AccordionGuy”, says “/migrate”. The follow-up comment, by the user “packfiles-warp”, says “@AccordionGuy, your migration’s in progress! We’ll let you know when it’s complete.”"><figcaption><p>The comments section of the page for the <em>TailwindTraders-Website</em> issue.</p></figcaption></figure>

Warp — which will have the user name **packfiles-warp** — always provides a response to your commands as a follow-up comment. In the example above, it’s notifying you that the migration process has begun.

It typically takes a few minutes to perform a migration. Let’s use this time to watch the migration’s progress.

🛠️ Switch to _Migration HQ_’s _Actions_ page by clicking the **Actions** tab:

<figure><img src="../../.gitbook/assets/image (17).png" alt="Migration HQ’s Actions page with a new active Warp Runner Agent. "><figcaption><p><em>Migration HQ</em>’s <em>Actions</em> page.</p></figcaption></figure>

You’ll see a new Warp Runner Agent running the workflow that performs the migration:

<figure><img src="../../.gitbook/assets/image (21).png" alt="The Warp Runner Agent, up close." width="375"><figcaption></figcaption></figure>

🛠️ Click on the Runner Agent to get a closer look at what it’s doing.

You’ll see the Runner Agent’s page:

<figure><img src="../../.gitbook/assets/image (19).png" alt="The Warp Runner Agent’s page."><figcaption><p>The Warp Runner Agent’s page.</p></figcaption></figure>

Let’s get an even closer look at what the Runner Agent is doing.

🛠️ Click on the job that the Runner Agent is running — it’s any of the objects onscreen labeled **Packfiles Warp Runner Agent** that has a spinning yellow icon beside it:

<figure><img src="../../.gitbook/assets/image (20).png" alt="The Warp Runner Agent up close." width="303"><figcaption></figcaption></figure>

You’ll go to a page where you can see the log files that the job is generating in real time:

<figure><img src="../../.gitbook/assets/image (22).png" alt="The logs for the Warp Runner Agent."><figcaption><p>The logs for the Warp Runner Agent, while the Agent is running.</p></figcaption></figure>

A couple of minutes later, the migration will be complete. You’ll know this has happened when the Runner Agent’s icon changes from spinning and yellow to a static green checkmark:

<figure><img src="../../.gitbook/assets/image (23).png" alt="The logs for the Warp Runner Agent, after the Agent has completed its task."><figcaption><p>The logs for the Warp Runner Agent, after the Agent has completed its task.</p></figcaption></figure>

🛠️ Click the **Actions** tab to return to the top level of the _Actions_ page.

You’ll see that the Runner Agent completed its tasks:

<figure><img src="../../.gitbook/assets/image (18).png" alt="Migration HQ’s Actions page after the Warp Runner Agent has completed its task."><figcaption><p><em>Migration HQ</em>’s <em>Actions</em> page.</p></figcaption></figure>

### Examine Your Migrated Repository

With the Runner Agent’s tasks complete, your repository has been migrated! Let’s look at its issue.

🛠️ Click the **Issues** tab to view the _Issues_ page.

You’ll see something like this:

<figure><img src="../../.gitbook/assets/image (24).png" alt="Migration HQ’s &#x22;Issues&#x22; page, with the open issues list displayed. The open issues list displays 4 items."><figcaption><p><em>Migration HQ</em>’s <em>Issues</em> page — the open issues.</p></figcaption></figure>

Notice that:

* There’s one less item in the open issues list, and
* There one new item in the formerly empty closed issues list.

🛠️ Click the **Closed** tab to view the closed issues list.

You’ll see the issue for the newly migrated repository:

<figure><img src="../../.gitbook/assets/image (26).png" alt="Migration HQ’s &#x22;Issues&#x22; page, with the closed issues list displayed. The closed issues list displays 1 item."><figcaption><p><em>Migration HQ</em>’s <em>Issues</em> page — the closed issues.</p></figcaption></figure>

🛠️ Click the issue to view its details:

<figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

You’ll see that the issue has been updated:

<figure><img src="../../.gitbook/assets/image (28).png" alt="The updated page for the &#x22;TailwindTraders-Website&#x22; issue. Its content now indicates that the repository has been migrated."><figcaption><p>The updated page for the <em>TailwindTraders-Website</em> issue.</p></figcaption></figure>

🛠️ Scroll to the comments section at the bottom of the page.

You’ll see a new comment from Warp, followed by a new notification:

<figure><img src="../../.gitbook/assets/image (30).png" alt="The newest comment on the &#x22;TailwindTraders-Website&#x22; issue page. The comment says &#x22;@AccordionGuy, your migration was successful. Visit your new code’s home at TailwindTraders.TailwindTraders-Website.&#x22;"><figcaption><p>The newest comment on the <em>TailwindTraders-Website</em> issue page.</p></figcaption></figure>

The comment informs you that the migration was successful and provides a link to the newly migrated repository.

The notification below the comment informs you that Warp automatically closed this issue.

🛠️ Confirm that the migration was successful by clicking the link in the comment. In this example, the link is the text **Tailwind-Traders.TailwindTraders-Website**.

Here’s what the example migrated repository looks like:

<figure><img src="../../.gitbook/assets/image (32).png" alt="The &#x22;Code&#x22; page for the migrated Tailwind-Traders repository."><figcaption><p>The migrated Tailwind-Traders repository.</p></figcaption></figure>

{% hint style="success" %}
🙌 Congratulations — you did it! 🙌&#x20;

You successfully migrated a repository!
{% endhint %}
