---
icon: microchip
description: How Warp does what it does.
hidden: true
---

# Runner Agent

### Overview

To perform the various tasks that make up the migration process, Warp employs GitHub hosted runners — pre-configured virtual machines provided by GitHub to run workflows. These are Warp’s Runner Agents.

For any Warp operation that takes more than a few seconds to execute, you should be able to open the **Actions** tab of the _Migration HQ_ repository for your project and see the Warp Runner Agent running that operation:

<figure><img src="../../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>

Some of the operations performed by Warp’s Runner Agents include:

* Verifying the credentials stored in your vault file.
* Scanning the source for repositories.
* Migrating a repository from the source to the destination.

### Viewing a Runner Agent’s Logs

To view a Runner Agent’s logs, click on its entry. This will bring up the runner’s details page:

<figure><img src="../../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>

In the **runner.yml** section,  click the button marked **Packfiles Warp Runner ...** to view the Runner Agent’s collection of logs:

<figure><img src="../../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

Click on any log title to expand it and view its contents. For example, here’s the log for the **Set up job** process:

<figure><img src="../../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>

### Example: Troubleshooting Using a Runner Agent’s Logs

In the event that Warp encounters a problem while migrating a repository, you’ll see a message like this in comments it the repository’s issue:

<figure><img src="../../.gitbook/assets/image (61).png" alt=""><figcaption></figcaption></figure>

If you see a message like this, expand the **Troubleshoot** section...

<figure><img src="../../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>

...then click the **Warp runner logs** link. You’ll be taken to the runner’s details page:

<figure><img src="../../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>

To view the Runner Agent’s collection of logs, click the button marked **Packfiles Warp Runner ...**&#x20;

<figure><img src="../../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

The search text field near the upper right corner of the page applies to all of the Runner Agent’s logs. A search for `Error` reveals the problem:

<figure><img src="../../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>

The end of line 429 shows what happened: `Name cannot end in .wiki`.&#x20;

A quick look at the issue’s body reveals the source of the problem: someone specified that the destination repository’s name as **PartsUnlimited.wiki**:

<figure><img src="../../.gitbook/assets/image (69).png" alt=""><figcaption></figcaption></figure>

ℹ️ GitHub repository names cannot end with **.wiki**; this is because it automatically creates a wiki for each repository using the repository’s name followed by the **.wiki** extension.

Fortunately, the solution is simple: rename the destination repository using the /rename-destination slash command so that it doesn’t end with **.wiki**.
