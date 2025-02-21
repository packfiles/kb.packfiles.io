---
icon: '4'
---

# Set Up Your Vault

### Objective

Now that you’ve gathered your source and destination credentials, you need to make them available to Warp so that it can perform migrations.&#x20;

You also need to ensure that these credentials are secured so that only Warp can use them. You’ll do this by setting up a _Vault_ — an encrypted file containing the credentials. To decrypt these credentials, you’ll provide Warp with the _Vault key_, the decryption key for the Vault file.

In this section, you’ll set up the Vault by creating the Vault file, creating a Vault key, pushing the Vault file to _Migration HQ_, and installing the Vault key as a secret in _Migration HQ_. You’ll do all this by using the GitHub CLI application with the Warp command-line extension and confirm it was done by looking at the updates to _Migration HQ_.

**At the end of this section, you will have a Vault file uploaded to&#x20;**_**Migration HQ**_**, which will provide Warp with the credentials necessary for performing your migrations.**

{% include "../../.gitbook/includes/search-for-the-emoji-if....md" %}

### Create the Vault File

🛠️ Open a command-line terminal on your computer, using the _Terminal_ application on macOS or Linux, or _Command Prompt_ or _PowerShell_ on Windows and change to the directory containing the cloned _Migration HQ_ repository.

🛠️ Run the following command, which starts the Warp command-line application that sets up the Vault:

```bash
gh warp vault setup
```

You will see the “Welcome” text pictured below:

<figure><img src="../../.gitbook/assets/image (77).png" alt="The “Credential Vault Setup” screen. Its text reads: “Welcome to credential vault setup! The next screen will walk you through the process of configuring the credential vault for providers connected to the Hypotheticorp11/Migration-HQ Project. To proceed, press Enter. When you&#x27;re done, you&#x27;ll be prompted to securely save the encryption key in your password manager.” The text is followed by an “Ok” button."><figcaption><p>The opening screen.</p></figcaption></figure>

🛠️ Press the **Enter** or **Return** key to continue.

You will see the _Configure Providers_ menu, which lets you add, update, and delete tokens for various source control providers:

<figure><img src="../../.gitbook/assets/image (78).png" alt="The “Configure Providers” menu screen. The “Add a New Provider” menu item is selected."><figcaption><p>The <em>Configure Providers</em> menu.</p></figcaption></figure>

🛠️ The default option, **Add a New Provider**, is the one you want. Press the **Enter** or **Return** key to select this option.

You will be taken to the _Add Provider Credentials_ menu:

<figure><img src="../../.gitbook/assets/image (81).png" alt="The “Add Provider Credentials&#x22; menu screen. The “Azure DevOps” menu item is selected."><figcaption><p>The <em>Add Provider Credentials</em> menu.</p></figcaption></figure>

🛠️ Let’s add the personal access token for Azure DevOps first. Since **Azure DevOps** is the default option, simply press the **Enter** or **Return** key to select it.

You’ll see this text, which explains that you’re about to configure an Azure DevOps provider:

<figure><img src="../../.gitbook/assets/image (80).png" alt="The “Credential Vault Setup” screen. Its text reads: “To authenticate to this Azure DevOps provider, we&#x27;ll need a Personal Access Token (PAT). The Personal Access Token will be used for all migration processes related to this provider. To learn more about Azure DevOps Personal Access Tokens, please visit our setup guide at https://pack.fm/ado-pat-setup.” The text is followed by a “Next” button."><figcaption><p>The opening screen for the "Configure an Azure DevOps Provider" process.</p></figcaption></figure>

🛠️ Press the **Enter** or **Return** key to continue.

You will now be prompted to enter the personal access token you created in Azure DevOps:

<figure><img src="../../.gitbook/assets/image (82).png" alt="The “Personal Access Token&#x22; screen. The “Your PAT” text entry area has not yet been filled in."><figcaption><p>The <em>Personal Access Token</em> screen.</p></figcaption></figure>

🛠️ Paste your Azure DevOps personal access token into the text area marked **Your PAT**...

<figure><img src="../../.gitbook/assets/image (83).png" alt="The “Personal Access Token&#x22; screen. The “Your PAT” text entry has been filled, with the PAT obscured by asterisks."><figcaption><p>The <em>Personal Access Token</em> screen, with the PAT filled in.</p></figcaption></figure>

🛠️ ...then press the **Enter** or **Return** key to continue.

The next step is to specify the access scope for the Azure DevOps personal access token:

<figure><img src="../../.gitbook/assets/image (84).png" alt="The “Access Scope&#x22; menu screen. The “Single organization access” menu item is selected."><figcaption><p>The <em>Access Scope</em> menu.</p></figcaption></figure>

🛠️ Select **Single organization access** using the ⬆️ and ⬇️ keys, then press the **Enter** or **Return** key.

You’ll be asked to enter the Azure Devops organization slug, which you copied when you were creating the personal access token for your Azure DevOps organization. In this example, the slug is `joey-ado-testing`:

<figure><img src="../../.gitbook/assets/image (85).png" alt="The “Organization Slug&#x22; screen. The organization slug text entry area is empty."><figcaption><p>The <em>Organization Slug</em> screen.</p></figcaption></figure>

🛠️ Paste or enter the organization slug into the text area marked **ado-organization-slug**...

<figure><img src="../../.gitbook/assets/image (86).png" alt="The “Organization Slug&#x22; screen. The organization slug text entry area now contains the text “joey-ado-testing”."><figcaption><p>The <em>Organization Slug</em> screen, with the organization slug filled in.</p></figcaption></figure>

🛠️ ...then press the **Enter** or **Return** key to continue.

You’ll then be asked to specify the number of days until the token expires:

<figure><img src="../../.gitbook/assets/image (87).png" alt="The “Token Expiration” screen. The token expiration text entry area contains the text “30”."><figcaption><p>The <em>Token Expiration</em> screen.</p></figcaption></figure>

🛠️ Enter **30**, then press the **Enter** or **Return** key.

Finally, you’ll be asked to confirm the information you’ve entered:

<figure><img src="../../.gitbook/assets/image (88).png" alt="The “Confirmation” screen. It says that the application will apply the configuration based on the Personal Access Token, token access scope (single organization), organization slug (joey-ado-testing), and days until token expiration (30). There are “Yes” and “No” buttons at the end."><figcaption><p>The <em>Confirmation</em> screen.</p></figcaption></figure>

🛠️ Press **y** to confirm that the information is correct.

It’s time to add the personal access token for GitHub. You’ll see the _Configure Providers_ menu again:

<figure><img src="../../.gitbook/assets/image (79).png" alt="The “Configure Providers” menu screen. The “Add a New Provider” menu item is selected."><figcaption><p>The <em>Configure Providers</em> screen.</p></figcaption></figure>

🛠️ Once again, the default option, **Add a New Provider**, is the one you want. Press the **Enter** or **Return** key to select this option.

<figure><img src="../../.gitbook/assets/image (89).png" alt="The “Add Provider Credentials&#x22; menu screen. The “GitHub [Destination]” menu item is selected."><figcaption><p>The <em>Add Provider Credentials</em> menu.</p></figcaption></figure>

🛠️ Select **GitHub \[Destination]** using the ⬆️ and ⬇️ keys, then press the **Enter** or **Return** key.

You’ll see this text, which explains that you’re about to configure a GitHub destination:

<figure><img src="../../.gitbook/assets/image (90).png" alt="The “Configure GitHub Destination” screen. Its text reads: “To authenticate to this GitHub destination, we&#x27;ll need a Personal Access Token (PAT). The Personal Access Token will be used for all migration processes related to this destination. To learn more about GitHub destination Personal Access Tokens, please visit our setup guide at https://pack.fm/gh-dest-pat-setup.” The text is followed by a “Next” button."><figcaption><p>The opening screen for the "Configure a GitHub Provider" process.</p></figcaption></figure>

🛠️ Press the **Enter** or **Return** key to continue.

You will now be prompted to enter the personal access token you created in GitHub:

<figure><img src="../../.gitbook/assets/image (91).png" alt="The “Personal Access Token&#x22; screen. The “Your PAT” text entry area is empty."><figcaption><p>The <em>Personal Access Token</em> screen.</p></figcaption></figure>

🛠️ Paste your GitHub personal access token into the text area marked **Your PAT**...

<figure><img src="../../.gitbook/assets/image (92).png" alt="The “Personal Access Token&#x22; screen. The “Your PAT” text entry has been filled, with the PAT obscured by asterisks."><figcaption><p>The <em>Personal Access Token</em> screen, with the PAT filled in.</p></figcaption></figure>

🛠️ ...then press the **Enter** or **Return** key to continue.

You’ll be asked to enter the GitHub organization slug, which you copied when you were creating the personal access token for your GitHub organization.

<figure><img src="../../.gitbook/assets/image (93).png" alt="The “Organization Slug&#x22; screen. The organization slug text entry area is empty."><figcaption><p>The <em>Organization Slug</em> screen.</p></figcaption></figure>

In this example, the slug is `Hypotheticorp01`:

<figure><img src="../../.gitbook/assets/image (94).png" alt="The “Organization Slug&#x22; screen. The organization slug text entry area now contains the text “Hypotheticorp01”."><figcaption><p>The <em>Organization Slug</em> screen, with the organization slug filled in.</p></figcaption></figure>

🛠️ Paste or enter the organization slug into the text area marked **destination-organization-slug**, then press the **Enter** or **Return** key to continue.

You’ll then be asked to specify the number of days until the token expires:

<figure><img src="../../.gitbook/assets/image (95).png" alt="The “Token Expiration” screen. The token expiration text entry area contains the text “0”."><figcaption><p>The <em>Token Expiration</em> screen.</p></figcaption></figure>

🛠️ Enter **30**, then press the **Enter** or **Return** key.

Finally, you’ll be asked to confirm the information you’ve entered:

<figure><img src="../../.gitbook/assets/image (96).png" alt="The “Confirmation” screen. It says that the application will apply the configuration based on the Personal Access Token, GitHub organization slug (Hypotheticorp01), and days until token expiration (0). There are “Yes” and “No” buttons at the end."><figcaption><p>The <em>Confirmation</em> screen.</p></figcaption></figure>

🛠️ Press **y** to confirm that the information is correct.

You will return to the _Configure Providers_ menu:

<figure><img src="../../.gitbook/assets/image (97).png" alt="The “Configure Providers” menu screen. The “Exit and Save Changes” menu item is selected."><figcaption><p>The <em>Configure Providers</em> menu.</p></figcaption></figure>

🛠️ Select **Exit and Save Changes** using the ⬆️ and ⬇️ keys, then press the **Enter** or **Return** key.

This will create the Vault file, which needs to be committed and pushed to the _Migration HQ_ repository. You will see this prompt:

<figure><img src="../../.gitbook/assets/image (98).png" alt="The “Commit and Push Changes” menu screen. The “Yes” menu item is selected."><figcaption><p>The <em>Commit and Push Changes</em> menu.</p></figcaption></figure>

🛠️ Use the default option, **Yes**, then press the **Enter** or **Return** key.

You will see the _Save Your Vault Key_ prompt:

<figure><img src="../../.gitbook/assets/image (99).png" alt="The “Save Your Vault Key” screen. It displays the key for the vault file and instructs the user to save this key. The user is also instructed not to skip this step, as this is the only time the key will be shown to them."><figcaption><p>The <em>Save Your Vault Key</em> screen.</p></figcaption></figure>

🛠️ Just as you did with the personal access token in Azure DevOps and GitHub, copy the Vault key and save it in a safe place — preferably a password manager. You will need it to unlock the personal access tokens that were encrypted into the vault.

🛠️ After you have copied and saved the Vault key, press the **Enter** or **Return** key to continue.

You’ll see the final message:

<figure><img src="../../.gitbook/assets/image (100).png" alt="The closing screen. Its text reads: “All done! Your credentials vault has been saved to ./config/vault.age. Next, install your vault master key in your Migration HQ’s Actions secrets by running ‘gh warp vault place’.”"><figcaption><p>The closing screen.</p></figcaption></figure>

At this point:

* The Azure DevOps and GitHub personal access tokens have been encrypted into the Vault file (`config/vault.age` on macOS and Linux, `config\vault.age` on Windows)
* The Vault file has been committed and pushed to the _Migration HQ_ repository.

### Check the Vault File

To ensure that your Vault File contains the correct credentials, we’ve included a utility to check it. Let’s use it now.

🛠️ Run the following command, which starts the Warp command-line application that checks the Vault file:

```
gh warp vault check
```

You’ll be greeting with this text asking for your Vault key:

<figure><img src="../../.gitbook/assets/image (113).png" alt="The opening screen, where the user is prompted to enter the key for the vault file in the current vault directory."><figcaption><p>The opening screen.</p></figcaption></figure>

🛠️ Paste the Vault key into the text area...

<figure><img src="../../.gitbook/assets/image (114).png" alt="The opening screen. The text entry area has been filled, with the vault key obscured by asterisks."><figcaption><p>The opening screen, with the vault key pasted in.</p></figcaption></figure>

🛠️ ...then press the **Enter** or **Return** key to continue.

The utility will check the credentials in your Vault file. If the credentials are valid, you’ll see this display with the text **All credentials are valid**, as shown below:

<figure><img src="../../.gitbook/assets/image (116).png" alt="The closing screen. It displays that the vault contains credentials for Azure DevOps and its accessible organizations (joey-ado-testing) and for GitHub, for which all required scopes are present."><figcaption><p>The closing screen.</p></figcaption></figure>

🛠️ If you see the **All credentials are valid** message, proceed to the next step. Otherwise, repate the [_Create the Vault File_](set-up-your-vault.md#create-the-vault-file) step.

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

You _could_ do this manually by copying the Vault key and pasting it into the _Migration HQ_ repository’s [_Secrets_](https://docs.github.com/en/actions/security-for-github-actions/security-guides/using-secrets-in-github-actions) section. However, Warp provides a command-line application that will do this for you. Let’s use it.

🛠️ Run the following command, which starts the Warp command-line application that stores the Vault key in the _Migration HQ_ repository:

```bash
gh warp vault place
```

You’ll be greeted with the following text:

<figure><img src="../../.gitbook/assets/image (101).png" alt="The opening screen. Its text reads “Install Runner Credentials Vault Master Key — Welcome! This command will install your credential vault master key into the Hypotheticorp11/Migration-HQ repository&#x27;s GitHub Actions secrets. This step is necessary for the Migration Runner to decrypt and use your Project&#x27;s encrypted credential vault. You&#x27;ll only need to do this once, or any time you&#x27;ve rotated your master key. To proceed, press Enter. You&#x27;ll be prompted to provide your encryption key.”  The text is followed by an “Ok” button."><figcaption><p>The opening screen.</p></figcaption></figure>

🛠️ Press the **Enter** or **Return** key to continue.

You’ll be prompted to enter your Vault key:

<figure><img src="../../.gitbook/assets/image (102).png" alt="The &#x22;Decrypt Credentials Vault&#x22; screen, where the user is prompted to enter the key for the Vault file in the current Vault directory."><figcaption><p>The <em>Decrypt Credentials Vault</em> screen.</p></figcaption></figure>

🛠️ Paste the Vault key into the text area...

<figure><img src="../../.gitbook/assets/image (103).png" alt="The &#x22;Decrypt Credentials Vault&#x22; screen. The text entry area has been filled, with the Vault key obscured by asterisks."><figcaption><p>The <em>Decrypt Credentials Vault</em> screen, with the Vault key pasted in.</p></figcaption></figure>

🛠️ ...then press the **Enter** or **Return** key to continue.

The app will store your Vault key into the _Migration HQ_ repository’s secrets and display this message:

<figure><img src="../../.gitbook/assets/image (104).png" alt="The closing screen. Its text reads “All done! Your credentials vault for Hypotheticorp01/Migration-HQ is ready to rock.”"><figcaption><p>The closing screen.</p></figcaption></figure>

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
You’re ready to [scan your source for repositories](scan-your-source-for-repositories.md).
{% endhint %}

