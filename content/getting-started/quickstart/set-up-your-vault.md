---
description: >-
  How to create your Vault, a secure place to store the credentials for your
  migration.
icon: '3'
---

# Set Up Your Vault

### Objective

Now that you’ve gathered your source and destination credentials, you need to make them available to Warp so that it can perform migrations.&#x20;

You also need to ensure that these credentials are secured so that only Warp can use them. You’ll do this by setting up a _Vault_ — an encrypted file containing the credentials. To decrypt these credentials, you’ll provide Warp with the _Vault key_, the decryption key for the Vault file.

In this section, you will:

* Set up your Project's Vault by creating the Vault file
* Push the Vault file to _Migration HQ_, and&#x20;
* Installing the Vault key as a secret in _Migration HQ_.&#x20;

You’ll do all this by using the Warp Vault desktop app and GitHub.com, and confirm it was done by looking at the updates to _Migration HQ_.

**At the end of this section, you will have a Vault file uploaded to&#x20;**_**Migration HQ**_**, which will provide Warp with the credentials necessary for performing your migrations.**

{% include "../../.gitbook/includes/search-for-the-emoji-if....md" %}

### Before You Begin

If you haven't already, you'll need to [install Warp Vault](../../using-warp/warp-vault/download-warp-vault/) on your local machine before proceeding with the following steps. &#x20;

{% include "../../.gitbook/includes/warp-vault-demo.md" %}

### Create Your Vault

🛠️ To kick things off, you'll need to create a Vault for your Migration Project. Open the Warp Vault application on your machine, expand the **Add Menu**, and choose "Create Vault".

{% embed url="https://static-pub.packfiles.io/knowledge_base/guides/vault_setup/Create%20Vault.mp4" %}
Creating a New Vault
{% endembed %}

🛠️ In the window that appears, click on the button to **Select a Directory**. You'll need to choose the **config** folder inside of the local clone of your **Migration HQ repository**.

{% hint style="warning" %}
It's important to get this right. If you don't choose the **config** folder in your local **Migration HQ** clone, Warp won't be able to access your credentials in later steps.
{% endhint %}

{% embed url="https://static-pub.packfiles.io/knowledge_base/guides/vault_setup/Select%20Vault%20File%20Directory.mp4" %}
Selecting a Vault's Location on Disk
{% endembed %}

🛠️ After choosing the directory to save your Vault, you can choose an **Icon**, give your Vault a **Name**, and a **Description**. These fields are local to your machine, and help you identify your Vault in the list (if you have multiple).

{% embed url="https://static-pub.packfiles.io/knowledge_base/guides/vault_setup/Create%20Vault%20Second%20Step.mp4" %}
Filling in a Vault's Name and Description
{% endembed %}

🛠️ Finally, after clicking **Create**, you'll be presented with your Vault's Master Key. Store this key in a secure location, such as your password manager. You'll need it to complete setup and make changes to your Vault's credentials in the future.

{% hint style="warning" %}
Securely store your Master Key in a password manager. **If you lose track of it, the contents of your Vault will be lost**, and you won't be able to proceed with the rest of the setup process.
{% endhint %}

{% embed url="https://static-pub.packfiles.io/knowledge_base/guides/vault_setup/Unlock%20Vault.mp4" %}
Unlocking a Vault with its Master Key
{% endembed %}

### Add Credentials to Your Vault

Your Vault has been created— congratulations! The next step is to **add credentials** to it.&#x20;

In order to migrate your repositories, you must provide Warp with two key sets of credentials:

1. Credentials authorizing access to the repositories at the source.
2. Credentials authorizing the creation of new repositories at the destination organization in GitHub.

🛠️  First, let’s get the credentials for the source — that is, the system that you’re migrating repositories _from_.

{% hint style="success" %}
For a list of credential types supported by Warp Vault and how to configure them, refer to the [Supported Credential Providers](../../using-warp/warp-vault/supported-credential-providers/) page in this document.
{% endhint %}

🛠️ You'll also need the credentials for your destination — that is, the system that you’re migrating repositories _to_.&#x20;

You'll need to configure a separate GitHub Personal Access Token to allow Warp to migrate repositories and data into your destination environment. For configuration instructions, refer to the [GitHub (Destination)](../../using-warp/warp-vault/supported-credential-providers/github-destination.md) credential documentation.

Once your credentials have been collected, you'll be ready to add them to your Vault.

🛠️ Use the **Add Button** in Warp Vault to add each type of credential you need for your Migration Project. Selecting a credential type will add a new entry to your Vault, opening a form where you can edit its details and configuration.

{% embed url="https://static-pub.packfiles.io/knowledge_base/guides/vault_setup/Vault%20Add%20Providers.mp4" %}
Adding Credentials to Warp Vault
{% endembed %}

### Test Your Credentials

Now that you've added credentials to your Vault, the next step is to **test** them. This process ensures your credentials are ready to use with Warp, and that you'll be able to perform migrations successfully.&#x20;

Luckily, Warp Vault has an integrated credential testing feature that makes this process a breeze. An example of how to use this feature is shown in the video snippet below, and you can walk through the process in detail through the [Warp Vault demo](https://packfiles.navattic.com/ybw09zv).

🛠️ Use the **Credential Testing** feature of Warp Vault to test the credentials you've configured. When each credential you've configured has a **Green Check**, you can save your changes and proceed.

{% embed url="https://static-pub.packfiles.io/knowledge_base/guides/vault_setup/Test%20Credentials.mp4" %}
Testing Credentials in Warp Vault
{% endembed %}

### Commit and Push Your Vault File

Next, you'll need to commit and push your encrypted Vault to your Migration HQ repository.&#x20;

🛠️ Open your local clone of Migration HQ in your favorite Git client. Then add, commit, and push the file to your Migration HQ.

{% hint style="success" %}
#### Is this secure?

**Yes.** Warp's model for securely storing your secrets as an encrypted file in your Migration HQ repository follows [GitHub's published best practice guidelines](https://docs.github.com/en/actions/security-for-github-actions/security-guides/using-secrets-in-github-actions#storing-large-secrets) for managing large secrets on the platform.
{% endhint %}

{% embed url="https://static-pub.packfiles.io/knowledge_base/guides/vault_setup/Commit%20and%20Push%20Vault%20File.mp4" %}
Committing and Pushing a Vault to Migration HQ from VS Code
{% endembed %}

### Confirm That the Vault Was Pushed to Migration HQ

Just to be certain, let’s take a look at _Migration HQ_ to make sure that the Vault was actually pushed there.

🛠️ Open _Migration HQ_ in a browser tab or panel and select the _Code_ tab:

<figure><img src="../../.gitbook/assets/image (107).png" alt="The &#x22;Migration HQ&#x22; page in GitHub."><figcaption><p><em>Migration HQ</em>.</p></figcaption></figure>

🛠️ Look at the files in the directory and look at the `config` directory’s last commit message: “Update Vault.”&#x20;

Also, take note that its commit time is more recent than any of the other items in the repository.

🛠️ Open the `config` directory:

<figure><img src="../../.gitbook/assets/image (105).png" alt="Migration HQ&#x27;s &#x22;config&#x22; directory. The key item is the &#x22;vault.age&#x22; file."><figcaption><p>Migration HQ’s <em>config</em> directory.</p></figcaption></figure>

🛠️ Look at the Vault file — once again, it’s `vault.age`. Its last commit message and last commit date confirm that it was pushed to _Migration HQ_ at the end of the Vault creation process.

### Store the Vault Key in Migration HQ’s Secrets

The next step is to store the key for the Vault in the _Migration HQ_ repository. This will allow Warp’s GitHub Actions to access the personal access tokens you encrypted into the Vault, which in turn will allow them to migrate your repositories from Azure DevOps to GitHub.

You can do this manually by copying the Vault key and pasting it into the _Migration HQ_ repository’s [_Secrets_](https://docs.github.com/en/actions/security-for-github-actions/security-guides/using-secrets-in-github-actions) settings.&#x20;

{% embed url="https://static-pub.packfiles.io/knowledge_base/guides/vault_setup/Add%20Repository%20Secret.mp4" %}
Adding Your Master Key as a Migration-HQ Repository Secret
{% endembed %}



### Confirm that that Vault and Key are in Migration HQ

You should confirm that your Vault key was successfully stored in _Migration HQ_ by checking the repository’s _Secrets_ section in GitHub.

🛠️ Open a browser tab or window to the _Migration HQ_ repository in GitHub and click the **Settings** tab.

<figure><img src="../../.gitbook/assets/image (108).png" alt="&#x22;Migration HQ’s&#x22; &#x22;Settings&#x22; page. The key item is the &#x22;Secrets and variables&#x22; item in the left side menu."><figcaption><p><em>Migration HQ</em>’s <em>Settings</em> page.</p></figcaption></figure>

🛠️ In the menu on the left side of the page, select **Secrets and variables** to expand it, then select **Actions**:

<figure><img src="../../.gitbook/assets/image (109).png" alt="The &#x22;Secrets and variables&#x22; menu. The key item is the &#x22;Actions&#x22; menu item." width="334"><figcaption><p>The <em>Secrets and variables</em> menu.</p></figcaption></figure>

You will be taken to the _Actions secrets and variables_ page for _Migration HQ_ :

<figure><img src="../../.gitbook/assets/image (111).png" alt="&#x22;Migration HQ’s&#x22; repository secrets. It contains one secret, whose name is &#x22;PKFS_MASTER_KEY&#x22;."><figcaption><p><em>Migration HQ’s</em> repository secrets.</p></figcaption></figure>

🛠️ Check the _Repository secrets_ section and confirm that it contains a secret named `PKFS_MASTER_KEY`.

If you see the `PKFS_MASTER_KEY` secret, you have successfully stored the Vault key in _Migration HQ_. If not, you should run the `gh warp vault place` command again.

{% hint style="success" %}
With the Vault file and secret install in _Migration HQ_, Warp now has the credentials to access your source repositories and destination GitHub organization.\
\
You’re ready to [scan your source for repositories](scan-your-sources-for-repositories.md).
{% endhint %}

