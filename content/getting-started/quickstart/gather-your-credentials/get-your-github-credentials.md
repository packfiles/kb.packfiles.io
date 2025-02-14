---
icon: key
---

# Get Your GitHub Credentials

### Objective

For Warp to be able to migrate your repositories to GitHub, it needs two key pieces of information:

1. The destination organization slug, which is the part of the organization’s webpage’s URL that uniquely identifies the organization.
2. A Personal Access Token (PAT) for your GitHub user account, which grants the bearer the necessary privileges to migrate repositories to the organization.

**At the end of this section, you will have the slug for your GitHub organization and a Personal Access Token for your GitHub account.**

{% include "../../../.gitbook/includes/search-for-the-emoji-if....md" %}



### Get the Organization Slug

🛠️ Switch to the browser tab or window containing _Migration HQ._

Make a note of the URL in your browser’s address bar. The URL contains the _organization slug_, which is the part of the URL that uniquely identifies the organization. It’s the part of the URL after `github.com/` and before `/Migration-HQ`:

<figure><img src="../../../.gitbook/assets/09_Migration_HQ_browser_address_bar.png" alt="Close-up of the browser&#x27;s address bar, which displays the URL &#x22;github.com/Hypotheticorp01&#x22;." width="375"><figcaption><p>The browser's address bar,<br>while on the <em>Migration HQ</em> page.</p></figcaption></figure>

In this example, the URL for the organization’s page is:

```
github.com/Hypotheticorp01/Migration-HQ
```

The organization slug is the part that comes after `github.com/` and before `/Migration-HQ`, which means that this example’s organization slug is:

```
Hypotheticorp01
```

🛠️ Copy the organization slug from your browser’s address bar and paste it someplace safe — you’ll use it when you create the vault file.

### Generate a Personal Access Token for Your Account&#x20;

🛠️ Switch to the browser tab or window containing _Migration HQ_ and click on your profile picture (located near the top right of the page) so that this menu appears:

<figure><img src="../../../.gitbook/assets/image (24) (1).png" alt="The menu that appears when you click your profile picture. The key item in the menu is the &#x22;Settings&#x22; item." width="173"><figcaption><p>The menu that appears when you<br>click your profile picture.</p></figcaption></figure>

🛠️ Select **Settings** from the menu.

You will be taken to the _Settings_ page for your GitHub account:

<figure><img src="../../../.gitbook/assets/10_GitHub_account_settings_page.png" alt="The &#x22;Settings&#x22; page for the user&#x27;s GitHub account."><figcaption><p>GitHub account <em>Settings</em> page.</p></figcaption></figure>

🛠️ Scroll down the page until you see the **Developer settings** item appear in the list on the left side:

<figure><img src="../../../.gitbook/assets/11_Developer_setting_spage_scrolled_down.png" alt="The &#x22;Settings&#x22; page for the user&#x27;s GitHub account, scrolled farther down the page."><figcaption><p>GitHub account <em>Settings</em> page, scrolled farther down.</p></figcaption></figure>

🛠️ Click on **Developer settings**.

This will take you to the _Developer Settings_ page:

<figure><img src="../../../.gitbook/assets/12a Developer_settings_1.png" alt="The &#x22;Developer Settings&#x22; page."><figcaption><p>The <em>Developer Settings</em> page.</p></figcaption></figure>

🛠️ In the menu on the left side of the page, expand the **Personal access tokens** item:

<figure><img src="../../../.gitbook/assets/13a Personal access tokens menu.png" alt="The Personal access tokens menu." width="311"><figcaption><p>The <em>Personal access tokens</em> menu.</p></figcaption></figure>

&#x20;🛠️ Select **Tokens (classic)** from the menu.

You will end up at the _Personal access tokens (classic)_ page:

<figure><img src="../../../.gitbook/assets/14a Personal access tokens page.png" alt="The Personal access tokens (classic) page."><figcaption><p>The <em>Personal access tokens (classic)</em> page.</p></figcaption></figure>

Towards the top right of the page, you’ll see the **Generate new token** button.

🛠️ Click the **Generate new token** button to make its menu appear:

<figure><img src="../../../.gitbook/assets/image (70).png" alt="The Generate new token menu." width="375"><figcaption><p>The <em>Generate new token</em> menu.</p></figcaption></figure>

🛠️ ...then select **Generate new token (classic)** from the menu.

You will arrive at the _New personal access token (classic)_ page, where you’ll need to provide enough information to create a new personal access token:

<figure><img src="../../../.gitbook/assets/15_New_personal_access_token_form (1).png" alt=""><figcaption><p>The <em>New personal access token (classic)</em> page.</p></figcaption></figure>

🛠️ Enter a name or some other text to help you identify the token in the **Note** field. To make it easier to identify, we suggest you include “Warp” in the name:

<figure><img src="../../../.gitbook/assets/16a Note and expiration.png" alt="" width="375"><figcaption></figcaption></figure>

{% hint style="info" %}
For the purposes of this Quickstart, we’ll leave the **Expiration** field at the default value of 30 days.
{% endhint %}

🛠️ Under **Select scopes**, check the following boxes. Checking these boxes will automatically check their sub-boxes:

* **repo**
* **workflow**
* **write:packages**
* **delete:packages**
* **admin:org**

<figure><img src="../../../.gitbook/assets/17_scopes_1.png" alt=""><figcaption></figcaption></figure>

🛠️  Then scroll down the page and check these boxes. Once again, checking these boxes will automatically check their sub-boxes:

* **admin:repo\_hook**
* **admin:org\_hook**
* **delete\_repo**

<figure><img src="../../../.gitbook/assets/image (112).png" alt=""><figcaption></figcaption></figure>

Feel free to use the checklist below to double-check that you’ve checked all the necessary checkboxes. It’s important to make sure you’ve checked all of them!

* [ ] **repo**
* [ ] **workflow**
* [ ] **write:packages**
* [ ] **delete:packages**
* [ ] **admin:org**
* [ ] **admin:repo\_hook**
* [ ] **delete\_repo**

🛠️ Scroll to the bottom of the page and click the **Generate token** button:

<figure><img src="../../../.gitbook/assets/image (75).png" alt="" width="162"><figcaption></figcaption></figure>

You should now see this page, which will display the personal access token you just created:

<figure><img src="../../../.gitbook/assets/image (76).png" alt=""><figcaption><p>TThe <em>Personal access tokens (classic)</em> page, with the newly-created Personal Access Token.</p></figcaption></figure>

🛠️ Copy the token and **save it in a safe place** — preferably a password manager.

{% include "../../../.gitbook/includes/this-will-be-your-only-time....md" %}

{% hint style="success" %}
You now have the information needed to connect Warp to GitHub.

You should [confirm that you have all the credentials you need for migration](confirm-that-youve-gathered-your-credentials.md).
{% endhint %}
