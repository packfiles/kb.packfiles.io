---
icon: key
description: >-
  How to get your Azure DevOps organization slug and create an Azure DevOps
  Personal Access Token.
---

# Get Your Azure DevOps Credentials

### Objective

For Warp to be able to access the Azure DevOps repositories that you want to migrate, it needs two key pieces of information about the Azure DevOps organization containing those repositories:

1. The organization slug, which is the part of the organization’s webpage’s URL that uniquely identifies the organization.
2. A Personal Access Token (PAT), which grants access to the organization containing the repositories.

**At the end of this section, you will have the slug and Personal Access Token for your Azure DevOps organization.**

{% include "../../../.gitbook/includes/search-for-the-emoji-if....md" %}

### Get the Organization Slug&#x20;

🛠️ Sign in to Azure DevOps and navigate to the page for the organization containing the projects whose repositories you want to migrate:

<figure><img src="../../../.gitbook/assets/image (17) (1).png" alt="The organization page in Azure DevOps. The &#x22;Projects&#x22; tab is on display, and it contains 3 projects: &#x22;Parts Unlimited,&#x22; &#x22;Tailwind Traders,&#x22; and &#x22;First Project.&#x22;"><figcaption><p>The organization page in Azure DevOps.</p></figcaption></figure>

{% hint style="info" %}
The example Azure DevOps organization for this quickstart is **joey-ado-testing**.
{% endhint %}

Make a note of the URL in your browser’s address bar. The URL contains the _organization slug_, which is the part of the URL that uniquely identifies the organization. It’s the part of the URL after `dev.azure.com/`:

<figure><img src="../../../.gitbook/assets/image (18) (1).png" alt="Close-up of the browser&#x27;s address bar, which displays the URL &#x22;dev.azure.com/joey-ado-testing&#x22;." width="375"><figcaption><p>The browser's address bar,<br>while on the organization page in Azure Devops.</p></figcaption></figure>

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

It’s time to get a Personal Access Token.

🛠️ Near the top right corner of the page, you’ll see the  <img src="../../../.gitbook/assets/image (19) (1).png" alt="" data-size="line"> (_User Settings_) icon. Click it to reveal its menu:

<figure><img src="../../../.gitbook/assets/image (16) (1).png" alt="The menu that appears when you click the User Settings icon. The key item in the menu is the &#x22;Personal access tokens&#x22; item." width="363"><figcaption><p>The menu that appears<br>when you click the <em>User Settings</em> icon.</p></figcaption></figure>

🛠️  Select **Personal access tokens** from the menu.

You will see the _Personal Access Tokens_ page:

<figure><img src="../../../.gitbook/assets/image (20) (1).png" alt="The Personal Access Tokens page. It is empty and displays the text &#x22;You do not have any personal access tokens yet.&#x22; There are two identical &#x22;New Token&#x22; buttons on the page; one near the top right corner, and one in the middle."><figcaption><p>The <em>Personal Access Tokens</em> page.</p></figcaption></figure>

🛠️ Click any of the **New Token** buttons on the page.

A panel will appear, prompting you to create a new personal access token:

<figure><img src="../../../.gitbook/assets/image (21) (1).png" alt="The &#x22;Create a new personal access token&#x22; panel, which is a form. The &#x22;Name&#x22; field contains &#x22;Warp migration 1&#x22;, the &#x22;Organization&#x22; field contains &#x22;joey-ado-testing&#x22;, the &#x22;Expiration (UTC)&#x22; field contains &#x22;30 days&#x22; and the selected &#x22;Scopes&#x22; radio button is &#x22;Full access&#x22;." width="375"><figcaption><p>The <em>Create a new personal access token</em> panel.</p></figcaption></figure>

🛠️ In the **Name** field, enter a name for the token. To make it easier to identify, we suggest you include “Warp” in the name.

🛠️ Under **Scopes**, change the option to **Full access**.

{% hint style="info" %}
For the purposes of this Quickstart, we’ll leave the **Expiration** field at the default value of 30 days.
{% endhint %}

🛠️ Click the **Create** button.

You should now see the _Success!_ panel, which will display the personal access token you just created:

<figure><img src="../../../.gitbook/assets/image (22) (1).png" alt="The &#x22;Success!&#x22; panel, which is a form. There is a text field containing the Personal Access Token. There are instructions to copy the token now because Azure DevOps does not store it and the user will never be able to access its value again." width="375"><figcaption><p>The <em>Success!</em> panel.</p></figcaption></figure>

🛠️ Copy the token and **save it in a safe place** — preferably a password manager.

{% include "../../../.gitbook/includes/this-will-be-your-only-time....md" %}

🛠️ Click the **Close** button.

When you close the _Success!_ panel, you will be taken back to the _Personal Access Tokens_ page. You will see the personal access token you just created listed there:

<figure><img src="../../../.gitbook/assets/image (23) (1).png" alt="The Personal Access Tokens page, with the newly-created Personal Access Token. The page now has a list, containing one token: &#x22;Warp migration 1&#x22;, the token that was created just now."><figcaption><p>The <em>Personal Access Tokens</em> page, with the newly-created Personal Access Token.</p></figcaption></figure>

{% hint style="success" %}
You now have the information needed to connect Warp to Azure DevOps.

If you haven’t already done so, [get the GitHub information that Warp needs](get-your-github-credentials.md).
{% endhint %}
