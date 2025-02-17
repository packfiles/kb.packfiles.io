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

<figure><img src="../../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

🛠️ Press the **Enter** or **Return** key to continue.

You will see the _Configure Providers_ menu, which lets you add, update, and delete tokens for various source control providers:

<figure><img src="../../.gitbook/assets/image (78).png" alt=""><figcaption></figcaption></figure>

🛠️ The default option, **Add a New Provider**, is the one you want. Press the **Enter** or **Return** key to select this option.

You will be taken to the _Add Provider Credentials_ menu:

<figure><img src="../../.gitbook/assets/image (81).png" alt=""><figcaption></figcaption></figure>

🛠️ Let’s add the personal access token for Azure DevOps first. Since **Azure DevOps** is the default option, simply press the **Enter** or **Return** key to select it.

You’ll see this text, which explains that you’re about to configure an Azure DevOps provider:

<figure><img src="../../.gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>

🛠️ Press the **Enter** or **Return** key to continue.

You will now be prompted to enter the personal access token you created in Azure DevOps:

<figure><img src="../../.gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>

🛠️ Paste your Azure DevOps personal access token into the text area marked **Your PAT**...

<figure><img src="../../.gitbook/assets/image (83).png" alt=""><figcaption></figcaption></figure>

🛠️ ...then press the **Enter** or **Return** key to continue.

The next step is to specify the access scope for the Azure DevOps personal access token:

<figure><img src="../../.gitbook/assets/image (84).png" alt=""><figcaption></figcaption></figure>

🛠️ Select **Single organization access** using the ⬆️ and ⬇️ keys, then press the **Enter** or **Return** key.

You’ll be asked to enter the Azure Devops organization slug, which you copied when you were creating the personal access token for your Azure DevOps organization. In this example, the slug is `joey-ado-testing`:

<figure><img src="../../.gitbook/assets/image (85).png" alt=""><figcaption></figcaption></figure>

🛠️ Paste or enter the organization slug into the text area marked **ado-organization-slug**...

<figure><img src="../../.gitbook/assets/image (86).png" alt=""><figcaption></figcaption></figure>

🛠️ ...then press the **Enter** or **Return** key to continue.

You’ll then be asked to specify the number of days until the token expires:

<figure><img src="../../.gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>

🛠️ Enter **30**, then press the **Enter** or **Return** key.

Finally, you’ll be asked to confirm the information you’ve entered:

<figure><img src="../../.gitbook/assets/image (88).png" alt=""><figcaption></figcaption></figure>

🛠️ Press **y** to confirm that the information is correct.

It’s time to add the personal access token for GitHub. You’ll see the _Configure Providers_ menu again:

<figure><img src="../../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>

🛠️ Once again, the default option, **Add a New Provider**, is the one you want. Press the **Enter** or **Return** key to select this option.

<figure><img src="../../.gitbook/assets/image (89).png" alt=""><figcaption></figcaption></figure>

🛠️ Select **GitHub \[Destination]** using the ⬆️ and ⬇️ keys, then press the **Enter** or **Return** key.

You’ll see this text, which explains that you’re about to configure a GitHub destination:

<figure><img src="../../.gitbook/assets/image (90).png" alt=""><figcaption></figcaption></figure>

🛠️ Press the **Enter** or **Return** key to continue.

You will now be prompted to enter the personal access token you created in GitHub:

<figure><img src="../../.gitbook/assets/image (91).png" alt=""><figcaption></figcaption></figure>

🛠️ Paste your GitHub personal access token into the text area marked **Your PAT**...

<figure><img src="../../.gitbook/assets/image (92).png" alt=""><figcaption></figcaption></figure>

🛠️ ...then press the **Enter** or **Return** key to continue.

You’ll be asked to enter the GitHub organization slug, which you copied when you were creating the personal access token for your GitHub organization.

<figure><img src="../../.gitbook/assets/image (93).png" alt=""><figcaption></figcaption></figure>

In this example, the slug is `Hypotheticorp01`:

<figure><img src="../../.gitbook/assets/image (94).png" alt=""><figcaption></figcaption></figure>

🛠️ Paste or enter the organization slug into the text area marked **destination-organization-slug**, then press the **Enter** or **Return** key to continue.

You’ll then be asked to specify the number of days until the token expires:

<figure><img src="../../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>

🛠️ Enter **30**, then press the **Enter** or **Return** key.

Finally, you’ll be asked to confirm the information you’ve entered:

<figure><img src="../../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>

🛠️ Press **y** to confirm that the information is correct.

You will return to the _Configure Providers_ menu:

<figure><img src="../../.gitbook/assets/image (97).png" alt=""><figcaption></figcaption></figure>

🛠️ Select **Exit and Save Changes** using the ⬆️ and ⬇️ keys, then press the **Enter** or **Return** key.

This will create the Vault file, which needs to be committed and pushed to the _Migration HQ_ repository. You will see this prompt:

<figure><img src="../../.gitbook/assets/image (98).png" alt=""><figcaption></figcaption></figure>

🛠️ Use the default option, **Yes**, then press the **Enter** or **Return** key.

You will see the _Save Your Vault Key_ prompt:

<figure><img src="../../.gitbook/assets/image (99).png" alt=""><figcaption></figcaption></figure>

🛠️ Just as you did with the personal access token in Azure DevOps and GitHub, copy the Vault key and save it in a safe place — preferably a password manager. You will need it to unlock the personal access tokens that were encrypted into the vault.

🛠️ After you have copied and saved the Vault key, press the **Enter** or **Return** key to continue.

You’ll see the final message:

<figure><img src="../../.gitbook/assets/image (100).png" alt=""><figcaption></figcaption></figure>

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

<figure><img src="../../.gitbook/assets/image (113).png" alt=""><figcaption></figcaption></figure>

🛠️ Paste the Vault key into the text area...

<figure><img src="../../.gitbook/assets/image (114).png" alt=""><figcaption></figcaption></figure>

🛠️ ...then press the **Enter** or **Return** key to continue.

The utility will check the credentials in your Vault file. If the credentials are valid, you’ll see this display with the text **All credentials are valid**, as shown below:

<figure><img src="../../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>

🛠️ If you see the **All credentials are valid** message, proceed to the next step. Otherwise, repate the [_Create the Vault File_](set-up-your-vault.md#create-the-vault-file) step.

### Confirm That the Vault Was Pushed to Migration HQ

Just to be certain, let’s take a look at _Migration HQ_ to make sure that the Vault was actually pushed there.

🛠️ Open _Migration HQ_ in a browser tab or panel and select the _Code_ tab:

<figure><img src="../../.gitbook/assets/image (107).png" alt=""><figcaption></figcaption></figure>

🛠️ Look at the files in the directory and look at the `config` directory’s last commit message: “Update Vault.”&#x20;

Also, take note that its commit time is more recent than any of the other items in the repository.

🛠️ Open the `config` directory:

<figure><img src="../../.gitbook/assets/image (105).png" alt=""><figcaption></figcaption></figure>

🛠️ Look at the Vault file — once again, it’s `vault.age`. Its last commit message and last commit date confirm that it was pushed to _Migration HQ_ at the end of the Vault creation process.

### Store the Vault Key in Migration HQ’s Secrets

The next step is to store the key for the Vault in the _Migration HQ_ repository. This will allow Warp’s GitHub Actions to access the personal access tokens you encrypted into the Vault, which in turn will allow them to migrate your repositories from Azure DevOps to GitHub.

You _could_ do this manually by copying the Vault key and pasting it into the _Migration HQ_ repository’s [_Secrets_](https://docs.github.com/en/actions/security-for-github-actions/security-guides/using-secrets-in-github-actions) section. However, Warp provides a command-line application that will do this for you. Let’s use it.

🛠️ Run the following command, which starts the Warp command-line application that stores the Vault key in the _Migration HQ_ repository:

```bash
gh warp vault place
```

You’ll be greeted with the following text:

<figure><img src="../../.gitbook/assets/image (101).png" alt=""><figcaption></figcaption></figure>

🛠️ Press the **Enter** or **Return** key to continue.

You’ll be prompted to enter your Vault key:

<figure><img src="../../.gitbook/assets/image (102).png" alt=""><figcaption></figcaption></figure>

🛠️ Paste the Vault key into the text area...

<figure><img src="../../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>

🛠️ ...then press the **Enter** or **Return** key to continue.

The app will store your Vault key into the _Migration HQ_ repository’s secrets and display this message:

<figure><img src="../../.gitbook/assets/image (104).png" alt=""><figcaption></figcaption></figure>

### Confirm that that Vault and Key are in Migration HQ

You should confirm that your Vault key was successfully stored in _Migration HQ_ by checking the repository’s _Secrets_ section in GitHub.

🛠️ Open a browser tab or window to the _Migration HQ_ repository in GitHub and click the **Settings** tab.

<figure><img src="../../.gitbook/assets/image (108).png" alt=""><figcaption></figcaption></figure>

🛠️ In the menu on the left side of the page, select **Secrets and variables** to expand it, then select **Actions**:

<figure><img src="../../.gitbook/assets/image (109).png" alt="" width="334"><figcaption></figcaption></figure>

You will be taken to the _Actions secrets and variables_ page for _Migration HQ_ :

<figure><img src="../../.gitbook/assets/image (111).png" alt=""><figcaption></figcaption></figure>

🛠️ Check the _Repository secrets_ section and confirm that it contains a secret named `PKFS_MASTER_KEY`.

If you see the `PKFS_MASTER_KEY` secret, you have successfully stored the Vault key in _Migration HQ_. If not, you should run the `gh warp vault place` command again.

{% hint style="success" %}
With the Vault file and secret install in _Migration HQ_, Warp now has the credentials to access your source repositories and destination GitHub organization.\
\
You’re ready to [scan your source for repositories](scan-your-source-for-repositories.md).
{% endhint %}

