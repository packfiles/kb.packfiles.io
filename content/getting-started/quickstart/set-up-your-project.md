---
icon: '2'
---

# Set Up Your Project

In Warp, a Project is an object for managing the migration of repositories to GitHub. Typically, you’ll create a new project for a specific _migration engagement_, such as moving a collection of repositories for an organization, department, team, or development project.

In this section, you’ll set up a Project by creating it, installing the Warp GitHub app for the organization, and configuring the Project.

{% include "../../.gitbook/includes/search-for-the-emoji-if....md" %}

### Sign In to the Warp Web Application

<figure><img src="../../media/images/quickstart/new_project/warp_sign_in_page.png" alt=""><figcaption><p>Warp’s sign in page, located at <a href="https://warp.packfiles.io/">warp.packfiles.io</a>.</p></figcaption></figure>

🛠️ Open a browser tab or window to the [Warp web application](https://warp.packfiles.io) at [warp.packfiles.io](https://warp.packfiles.io).

🛠️ Click the **Sign in with GitHub** button and sign in to Warp using your GitHub account.

### Create a New Project

Upon signing in, you will be taken to Warp’s _Projects_ page, which lists you current migration projects.&#x20;

At the bottom of the list of projects, you’ll see the **Create a New Project** link.

<figure><img src="../../media/images/quickstart/new_project/warp_click_create_new_project_link.png" alt=""><figcaption><p>Warp’s <em>Projects</em> page, which you’ll see immediately after signing in.</p></figcaption></figure>

🛠️ Click the **Create a New Project** link.

A new section will appear below the link. This section provides instructions for what to do next, which is to install the Warp GitHub app into the GitHub organization where you will migrate your repositories:

<figure><img src="../../media/images/quickstart/new_project/warp_click_create_new_project_link_2.png" alt=""><figcaption><p>Creating a new project in Warp.</p></figcaption></figure>

🛠️ Click the **Install Warp from the GitHub Marketplace** button.

### Install the Warp Github App

A new browser will open to the GitHub Marketplace page for the Warp GitHub app:

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

🛠️ Click the **Add** button near the upper right corner of the page or scroll to the bottom of the page. You should see the following:

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

🛠️ In the **Account:** menu, select the account for the destination organization — that is, the organization that you will be migrating repositories to:

<figure><img src="../../.gitbook/assets/image (8).png" alt="" width="322"><figcaption></figcaption></figure>

{% hint style="info" %}
The example destination organization for this quickstart is **Hypotheticorp1234**.
{% endhint %}

🛠️ Click the **Install it for free** button.

You’ll be taken to the **Review Your Order** page:

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

🛠️ Review the order, then click the **Complete order** button.

You’ll go to the _Install Packfiles Warp_ page, which will show:

* That the Warp GitHub app will have access to all the repositories in the organization, and
* What read, read/write, and admin permissions it will have within the organization and its repositories.

<figure><img src="../../.gitbook/assets/image (10).png" alt="" width="375"><figcaption></figcaption></figure>

🛠️ Click the **Install** button at the bottom of the page.&#x20;

You will return to the Warp web app, and can proceed to the next step.

### Configure the Project

You will be at the _Welcome to Warp_ page:

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

🛠️ Click the **Next** button.

This will take to you the _Configure Your Project_ page:

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

You can do two things on this page:

1. You can set the name of your project, or choose to keep the default name.
2. You can invite people on your team to become members of the project.

{% hint style="info" %}
As the creator of the project, you don’t have to add yourself to the team. You are already a member of the project with _Admin_ access.
{% endhint %}

🛠️ For this quickstart, simply click the **Next** button.

You will arrive at the _Connect Your Sources_ page. You’ll use it in the process of connecting your source and GitHub accounts to Warp:

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

When you created the project, Warp created a repository named _Migration HQ_ for the GitHub organization that you selected earlier. _Migration HQ_ will be the user interface for managing your migrations. It will be where you issue commands to Warp and it will keep track of which repositories to migrate and which ones have already been migrated.

🛠️ Let’s visit _Migration HQ_. Click the **Migration HQ** button.

A new browser tab or window will open, and you should see the _Migration HQ_ page:

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

The files contained in _Migration HQ_ are configuration and credentials files that Warp will use in the migration process. You will need to clone _Migration HQ_ to your local computer, where you will create a _vault file_ containing the following:

* Credentials for accessing the repositories at the source (the place where you are migrating repositories _from_).
* Credentials for accessing the destination GitHub organization (the place where you are migrating repositories _to_).

After creating the vault file, Warp will automatically push it to _Migration HQ_, making the credentials available to Warp, enabling it to migrate your repositories.

🛠️ Clone the _Migration HQ_ repository to your local computer.

{% hint style="success" %}
You’ve successfully set up your project — nicely done!

Make sure that you’ve cloned _Migration HQ_ to your local computer, then proceed to the next step.
{% endhint %}

