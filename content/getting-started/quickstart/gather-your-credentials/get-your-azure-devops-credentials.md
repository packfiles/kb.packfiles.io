---
icon: key
---

# Get Your Azure DevOps Credentials

For Warp to be able to access the Azure DevOps repositories that you want to migrate, it needs two key pieces of information about the Azure DevOps organization containing those repositories:

1. The organization slug, which is the part of the organization’s webpage’s URL that uniquely identifies the organization.
2. A Personal Access Token (PAT), which grants access to the organization containing the repositories.

In this section, you will gather these two pieces of information.

{% include "../../../.gitbook/includes/search-for-the-emoji-if....md" %}

### Get the Organization Slug&#x20;

🛠️ Sign in to Azure DevOps and navigate to the page for the organization containing the projects whose repositories you want to migrate:

<figure><img src="../../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The example Azure DevOps organization for this quickstart is **joey-ado-testing**.
{% endhint %}

Make a note of the URL in your browser’s address bar. The URL contains the _organization slug_, which is the part of the URL that uniquely identifies the organization. It’s the part of the URL after `dev.azure.com/`:

<figure><img src="../../../.gitbook/assets/image (18).png" alt="" width="375"><figcaption></figcaption></figure>

In this example, the URL for the organization’s page is:

```
dev.azure.com/joey-ado-testing
```

The organization slug is the part that comes after `dev.azure.com/`, which means that this example’s organization slug is:

```
joey-ado-testing
```

🛠️ Copy the organization slug from your browser’s address bar and paste it someplace safe — you’ll use it when you create the vault file.

### Generate a Personal Access Token for Your Organization

It’s time to get a personal access token.

<figure><img src="../../../.gitbook/assets/image (16).png" alt="" width="363"><figcaption></figcaption></figure>

🛠️ Near the top right corner of the page, you’ll see the  <img src="../../../.gitbook/assets/image (19).png" alt="" data-size="line"> (_User Settings_) icon. Click it and select **Personal access tokens** from the menu that appears.

You will see the _Personal Access Tokens_ page:

<figure><img src="../../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

🛠️ Click any of the **New Token** buttons on the page.

A panel will appear, prompting you to create a new personal access token:

<figure><img src="../../../.gitbook/assets/image (21).png" alt="" width="375"><figcaption></figcaption></figure>

🛠️ In the **Name** field, enter a name for the token. To make it easier to identify, we suggest you include “Warp” in the name.

🛠️ Under **Scopes**, change the option to **Full access**.

{% hint style="info" %}
For the purposes of this Quickstart, we’ll leave the **Expiration** field at the default value of 30 days.
{% endhint %}

🛠️ Click the **Create** button.

You should now see the _Success!_ panel, which will display the personal access token you just created:

<figure><img src="../../../.gitbook/assets/image (22).png" alt="" width="375"><figcaption></figcaption></figure>

🛠️ Copy the token and **save it in a safe place** — preferably a password manager.

{% include "../../../.gitbook/includes/this-will-be-your-only-time....md" %}

🛠️ Click the **Close** button.

When you close the _Success!_ panel, you will be taken back to the _Personal Access Tokens_ page. You will see the personal access token you just created listed there:

<figure><img src="../../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
You now have the information needed to connect Warp to Azure DevOps.

If you haven’t already done so, get the GitHub information that Warp needs.
{% endhint %}
