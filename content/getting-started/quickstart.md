---
icon: rocket-launch
---

# Quickstart

This Quickstart will guide you through the process of migrating repositories from Azure DevOps to GitHub using Warp. You’ll create a new project, set up your Vault, connect your Azure DevOps and GitHub organizations to Warp, and migrate a repository from Azure DevOps to GitHub.

![Warp 'Sign In' page](../media/images/quickstart/intro/migration.png)

In this Quickstart, you will:

* Install the prerequisites
* Create a new project to migrate repositories from Azure DevOps to GitHub
* Get personal access tokens for Azure DevOps and GitHub
* Set up a vault to securely store the personal access tokens and a vault key to unlock them
* Connect Azure DevOps to Warp
* Migrate a repository from Azure DevOps to GitHub

Search for the 🛠️ emoji if you’d like to skim through this Quickstart’s content while focusing on the steps you need to follow to perform a migration.

### 1. Install the Prerequisites

Before you can start migrating repositories from Azure DevOps to GitHub, you need to install the following prerequisites:

1. **GitHub CLI (command-line interface) application**. Even if you have the GitHub dekstop application installed, you’ll need the GitHub CLI to use the Warp command-line extension.
2. **Warp command-line extension**. This is a GitHub CLI extension that you’ll use to set up the vault, the secure file that stores the access tokens for your GitHub account and the ADO organization you want to migrate repositories from.

If you already have these prerequisites installed, you can skip this section and move on to section 2, _Create a New Project_.

If you _don’t_ have these prerequisites installed, you’ll need to install them before you can proceed with the migration. Follow the steps below to install the prerequisites.

#### 1a. Install the GitHub CLI

First, see if the GitHub CLI is installed on your computer.

🛠️ Open your terminal application (on Windows, it’s _Windows PowerShell_ or _Command Prompt_; on macOS and Linux, the default terminal is named _Terminal_).

🛠️ Enter the following command:

```bash
gh --version
```

If the GitHub CLI is installed, you’ll see a message showing its version number and the URL for its release notes. Here’s an example:

```bash
gh version 2.63.1 (2024-12-03)
https://github.com/cli/cli/releases/tag/v2.63.1
```

If you see an error message instead, you’ll need to install the GitHub CLI. Go to the [GitHub CLI page](https://cli.github.com/) and follow the instructions there.

#### 1b. Install the Warp Command-line Extension

🛠️ Once you’ve confirmed that the GitHub CLI is installed on your computer, enter the following command to install the Warp command-line extension:

```bash
gh extension install packfiles/gh-warp
```

🛠️ Confirm that the Warp command-line extension is installed by running the following command in a terminal window:

```bash
gh warp
```

You should see this response:

```
      _ _ _                  
     | | | |___ ___ ___      
     | | | | .'|  _| . |     
     |_____|__,|_| |  _|     
Gets You To GitHub |_| vx.x.x
   With ❤️ From Packfiles.io 
                             
You're running the latest version of gh-warp (vx.x.x)
                                                     
GitHub migration superpowers, at your fingertips.

Usage:
  warp [command]

Available Commands:
  completion  Generate the autocompletion script for the specified shell
  help        Help about any command
  vault       Configure a Project Repository's credential vault

Flags:
  -h, --help      help for warp
  -v, --version   version for warp

Use "warp [command] --help" for more information about a command.
```

🙌 If you’ve made it this far, you’ve successfully installed the prerequisites using Warp.

### 2. Create a New Project

The next step is to create a _**Project**_, which in Warp is an object for managing the migration of repositories to GitHub. Typically, you’ll create a new project for a specific _migration engagement_, such as moving a collection of repositories for your own organization or for a client.

You’ll use the Warp web application to create the project.

![Warp 'Sign In' page. An arrow instructs the reader to click on the 'Sign in with GitHub' button.](../media/images/quickstart/new_project/warp_sign_in_page.png)

🛠️ Open a browser tab or window to the [Warp web application](https://warp.packfiles.io) at [warp.packfiles.io](https://warp.packfiles.io).

🛠️ Click the **Sign in with GitHub** button and sign in to Warp using your GitHub account.

You will be taken to the _Projects_ page, which lists the current migration projects. At the bottom of the list of projects, you’ll see the **Create a New Project** link.

![Warp 'Projects' page. An arrow instructs the reader to click the 'Create a New Project' link.](../media/images/quickstart/new_project/warp_click_create_new_project_link.png)

🛠️ Click the the **Create a New Project** link.

A new section will appear below the link. This section provides instructions for what to do next, which is to install the Warp GitHub app into the GitHub organization where you will migrate your repositories.

![GitHub 'Packfiles requires two-factor authentication' page](../media/images/quickstart/new_project/warp_click_install_warp_button.png)

🛠️ Click the the **Install Warp from the GitHub Marketplace** link.

You will arrive at the page for the Warp GitHub app:

![GitHub 'Packfiles Warp GitHub App' page](../media/images/quickstart/new_project/github_packfiles_warp_github_app.png)

🛠️ Click the **Configure** button to install Warp.

You will be shown a list of user and organization accounts where you can install Warp:

![GitHub 'Install Packfiles Warp' page](../media/images/quickstart/new_project/github_install_packfiles_warp_select_org.png)

🛠️ Select the organization account where Warp will be installed. This should be the organization where you’ll migrate the repositories _to_. In this example, the organization is **Hypotheticorp5678**.

After you select the organization, you will go to a page showing which repositories the Warp GitHub app will have access to (all of them) and what it will have read, write, and admin access to.

![GitHub 'Install Packfiles Warp' details page](../media/images/quickstart/new_project/github_install_packfiles_warp_install.png)

🛠️ Click the **Install** button.

You should automatically return to the _Projects_ page in the Warp web application:

![Warp 'Projects' page, with instructions to reload](../media/images/quickstart/new_project/warp_projects_page_reload.png)

🛠️ Click your browser’s **Reload** button.

You should arrive at the _Welcome to Warp_ page:

![Warp 'Welcome to Warp' page](../media/images/quickstart/new_project/warp_welcome_to_warp.png)

🛠️ Click the **Next** button.

This will take to you the _Configure Your Project_ page. You can do two things on this page:

1. You can set the name of your project, or choose to keep the default name.
2. You can invite people on your team to become members of the project.

![Warp 'Configure Your Project' page](../media/images/quickstart/new_project/warp_configure_your_project.png)

🛠️ For this quickstart, simply click the **Next** button.

ℹ️ As the creator of the project, you don’t have to add yourself to the team. You are already a member of the project with _Admin_ access.

The next page to appear is the _Connect Your Sources_ page. You’ll use it in the process of connecting your Azure DevOps and GitHub accounts to Warp.

![Warp Sign In page](../media/images/quickstart/new_project/warp_connect_your_sources.png)

When you created the project, Warp created a repository named _Migration HQ_ for the GitHub organization that you selected earlier. This repository will be the user interface for managing your migrations.

Your next task is to clone the repository to your local computer. You will then create a file containing your authorizations to access both your Azure DevOps organization and GitHub account, which Warp will use to migrate your repositories. Warp will then add that file to the local repository and push it to _Migration HQ_.

🛠️ Let’s visit _Migration HQ_. Click the **Migration HQ** button.

You will be taken to the _Migration HQ_ page:

![Warp Sign In page](../media/images/quickstart/new_project/github_migration-hq_initial.png)

🛠️ Clone the _Migration HQ_ repository to your local computer.

### 3. Generate Personal Access Tokens (PATs)

In order to migrate repositories from Azure DevOps to GitHub, you need to provide Warp with authorizations to access:

1. The Azure DevOps organization that contains the repositories you want to migrate, and
2. Your GitHub account.

You do this by generating Personal Access Tokens (PATs) for both of the above. Warp will use the authorization that these tokens provide to access the repositories in the Azure DevOps organization and migrate them to the destination GitHub organization.

#### 3a. Generate a PAT for Your Azure DevOps Organization

First, let’s generate a PAT for your Azure DevOps account.

![ADO 'Azure DevOps Organization's page](../media/images/quickstart/ado_pat/ado_organizations.png)

🛠️ Sign in to Azure DevOps and navigate to the _Organizations_ page. On that page, select the organization whose repositories you want to migrate to GitHub.

You will arrive at the page for the organization you selected.

![ADO organizations page](../media/images/quickstart/ado_pat/ado_organization.png)

🛠️ Click on the _User Settings_ icon near the top right corner of the page (it looks like a person with a gear) and select **Personal access tokens** from the menu that appears.

This will take you to the _Personal Access Tokens_ page:

![ADO 'Personal Access Tokens' page](../media/images/quickstart/ado_pat/ado_personal_access_tokens_initial.png)

🛠️ There will be at least one **New Token** button. Click any of them.

A panel will appear, prompting you to create a new personal access token:

![ADO 'Create a new personal access token' panel](../media/images/quickstart/ado_pat/ado_create_a_new_personal_access_token.png)

🛠️ In the **Name** field, enter a name for the token. To make it easier to identify, we suggest you include “Warp” in the name.

🛠️ Under **Scopes**, change the option to **Full access**.

For the purposes of this Quickstart, we’ll leave the **Expiration** field at the default value of 30 days.

🛠️ Click the **Create** button.

You should now see the _Success!_ panel, which will display the personal access token you just created:

![ADO 'Success!' panel](../media/images/quickstart/ado_pat/ado_new_pat_success.png)

🛠️ Copy the token and **save it in a safe place** — preferably a password manager. You will need it to connect your Azure DevOps account to Warp.

This will be your only time that this personal access token will be presented to you. Make sure you’ve copied it someplace safe before clicking the **Close** button!

🛠️ Click the **Close** button.

When you close the _Success!_ panel, you will be taken back to the _Personal Access Tokens_ page. You will see the personal access token you just created listed there:

![ADO 'Personal Access Tokens' page, now updated with new token](../media/images/quickstart/ado_pat/ado_personal_access_tokens_new_token.png)

You now have a personal access token that you can use to connect your Azure DevOps account to Warp.

#### 3b. Generate a PAT for Your GitHub Account

Let’s now generate a PAT for your GitHub account.

![GitHub 'Migration HQ' page](../media/images/quickstart/gh_pat/github_profile_picture_menu.png)

🛠️ Switch to GitHub, then click on your profile picture. Select **Settings** from the menu that appears.

You will be taken to the _Settings_ page for your GitHub account:

![GitHub user account 'Settings' page](../media/images/quickstart/gh_pat/github_select_developer_settings.png)

🛠️ In the left-hand menu, click on **Developer settings** (you may need to scroll down a bit).

This will take you to the _Developer settings_ page:

![GitHub 'Developer Settings' page](../media/images/quickstart/gh_pat/github_expand_pat_menu.png)

🛠️ In the left-hand menu, expand the **Personal access tokens** item, then select **Tokens (classic)**.

You will end up at the _Personal access tokens (classic)_ page:

![GitHub 'Personal access tokens (classic)' page](../media/images/quickstart/gh_pat/github_generate_new_token.png)

🛠️ Click the **Generate new token** button, then select **Generate new token (classic)** from the menu that appears.

You will arrive at the _New personal access token (classic)_ page, where you’ll need to provide enough information to create a new personal access token:

![GitHub 'New personal access token (classic)' page](../media/images/quickstart/gh_pat/github_new_pat_settings_1.png)

🛠️ Enter a name or some other text to help you identify the token in the **Note** field. To make it easier to identify, we suggest you include “Warp” in the name.

For the purposes of this Quickstart, we’ll leave the **Expiration** field at the default value of 30 days.

🛠️ Under **Select scopes**, check the following boxes, which will appear in this order:

* **repo**
* **workflow**
* **write:packages**
* **delete:packages**

🛠️ Scroll down a little further:

![Warp Sign In page](../media/images/quickstart/gh_pat/github_new_pat_settings_2.png)

🛠️ Also check the following:

* **admin:org**
* **admin:repo\_hook**
* **delete\_repo**

🛠️ Scroll to the bottom of the page:

![Warp Sign In page](../media/images/quickstart/gh_pat/github_new_pat_settings_3.png)

🛠️ Click the **Generate token** button.

You should now see this page, which will display the personal access token you just created:

![Warp Sign In page](../media/images/quickstart/gh_pat/github_personal_access_tokens_new_token.png)

🛠️ Just as you did with the personal access token in Azure DevOps, copy this new personal access token and save it in a safe place — preferably a password manager. You will need it to connect your GitHub account to Warp.

Once again, this will be your only time that this personal access token will be presented to you. Make sure you’ve copied it someplace safe before closing this web page!

### 4. Set Up the Vault

Now that you’ve generated personal access tokens for both your Azure DevOps organization and GitHub account, you need to make them available to Warp so that it can perform migrations, while securing them so that they are only available to Warp. You’ll do this by setting up a _vault_ — an encrypted file that stores the personal access tokens, which Warp will decrypt with a _vault key_.

🛠️ Open a command-line terminal on your computer, using the _Terminal_ application on macOS or Linux, or _Command Prompt_ or _PowerShell_ on Windows and change to the directory containing the cloned _Migration HQ_ repository.

🛠️ Run the following command, which starts the Warp command-line application that sets up the vault:

```bash
gh warp vault setup
```

You will see the “Welcome” text pictured below:

![Warp command-line 'Welcome' prompt](../media/images/quickstart/vault_setup/vault_setup_start.png)

🛠️ Press the **Enter** or **Return** key to continue.

You will see the _Configure Providers_ menu, which lets you add, update, and delete tokens for various source control providers:

![Warp command-line 'Configure Providers' menu](../media/images/quickstart/vault_setup/vault_setup_add_new_provider_1.png)

🛠️ The default option, **Add a New Provider**, is the one you want. Press the **Enter** or **Return** key to select this option.

![Warp command-line 'Add Provider Credentials' menu](../media/images/quickstart/vault_setup/vault_setup_select_add_ado_credentials.png)

🛠️ Let’s add the personal access token for Azure DevOps first. Since **Azure DevOps** is the default option, simply press the **Enter** or **Return** key to select it.

You’ll see this text, which explains that you’re about to configure an Azure DevOps provider:

![Warp command-line 'Configure an Azure DevOps provider' prompt](../media/images/quickstart/vault_setup/vault_setup_add_ado_credentials.png)

🛠️ Press the **Enter** or **Return** key to continue.

You will now be prompted to enter the personal access token you created in Azure DevOps:

![Warp command-line 'Personal Access Token' prompt](../media/images/quickstart/vault_setup/vault_setup_paste_ado_pat.png)

🛠️ Paste your Azure DevOps personal access token into the text area marked **Your PAT**...

![Warp command-line 'Personal Access Token' prompt, with obfuscated personal access token pasted in](../media/images/quickstart/vault_setup/vault_setup_pasted_ado_pat.png)

🛠️ ...then press the **Enter** or **Return** key to continue.

The next step is to specify the access scope for the Azure DevOps personal access token:

![Warp command-line 'Access Scope' prompt](../media/images/quickstart/vault_setup/vault_setup_ado_access_scope.png)

🛠️ Select **Single organization access** using the ⬆️ and ⬇️ keys, then press the **Enter** or **Return** key.

You’ll be asked to provide the slug for the Azure DevOps organization you want to connect to Warp:

![Warp command-line 'Organization Slug' prompt](../media/images/quickstart/vault_setup/vault_setup_paste_ado_org_slug.png)

🛠️ Paste or enter the organization slug into the text area marked **ado-organization-slug**...

![Warp command-line 'Organization Slug' prompt with organization slug pasted in](../media/images/quickstart/vault_setup/vault_setup_pasted_ado_org_slug.png)

🛠️ ...then press the **Enter** or **Return** key to continue.

You’ll then be asked to specify the number of days until the token expires:

![Warp command-line 'Token Expiration' prompt](../media/images/quickstart/vault_setup/vault_setup_enter_ado_pat_expiration.png)

🛠️ Enter **30**, then press the **Enter** or **Return** key.

Finally, you’ll be asked to confirm the information you’ve entered:

![Warp command-line 'Confirmation' prompt](../media/images/quickstart/vault_setup/vault_setup_confirm_ado_pat.png)

🛠️ Press **y** to confirm that the information is correct.

It’s time to add the personal access token for GitHub. You’ll see the _Configure Providers_ menu again:

![Warp command-line 'Configure Providers' menu](../media/images/quickstart/vault_setup/vault_setup_add_new_provider_2.png)

🛠️ Once again, the default option, **Add a New Provider**, is the one you want. Press the **Enter** or **Return** key to select this option.

![Warp command-line 'Add Provider Credentials' menu](../media/images/quickstart/vault_setup/vault_setup_select_add_github_credentials.png)

🛠️ Select **GitHub \[Destination]** using the ⬆️ and ⬇️ keys, then press the **Enter** or **Return** key.

You’ll see this text, which explains that you’re about to configure a GitHub destination:

![Warp command-line 'Configure GitHub Destination' menu](../media/images/quickstart/vault_setup/vault_setup_add_github_credentials.png)

🛠️ Press the **Enter** or **Return** key to continue.

You will now be prompted to enter the personal access token you created in GitHub:

![Warp command-line 'Personal Access Token' prompt](../media/images/quickstart/vault_setup/vault_setup_paste_github_pat.png)

🛠️ Paste your GitHub personal access token into the text area marked **Your PAT**...

![Warp command-line 'Personal Access Token' prompt with obfuscated personal access token pasted in](../media/images/quickstart/vault_setup/vault_setup_pasted_github_pat.png)

🛠️ ...then press the **Enter** or **Return** key to continue.

You’ll be asked to provide the slug for the GitHub organization you want to connect to Warp:

![Warp command-line 'Organization Slug' prompt](../media/images/quickstart/vault_setup/vault_setup_paste_github_org_slug.png)

🛠️ Paste or enter the organization slug into the text area marked **destination-organization-slug**...

![Warp command-line 'Organization Slug' prompt with organizational slug pasted in](../media/images/quickstart/vault_setup/vault_setup_pasted_github_org_slug.png)

🛠️ ...then press the **Enter** or **Return** key to continue.

You’ll then be asked to specify the number of days until the token expires:

![Warp command-line 'Token Expiration' prompt](../media/images/quickstart/vault_setup/vault_setup_enter_github_pat_expiration.png)

🛠️ Enter **30**, then press the **Enter** or **Return** key.

Finally, you’ll be asked to confirm the information you’ve entered:

![Warp command-line 'Confirmation' prompt](../media/images/quickstart/vault_setup/vault_setup_confirm_github_pat.png)

🛠️ Press **y** to confirm that the information is correct.

You will return to the _Configure Providers_ menu.

![Warp command-line 'Configure Providers' menu](../media/images/quickstart/vault_setup/vault_setup_exit_and_save_changes.png)

🛠️ You’ve already configured both Azure DevOps and GitHub; it’s time to save your changes and exit. Select **Exit and Save Changes** using the ⬆️ and ⬇️ keys, then press the **Enter** or **Return** key.

You will see the _Save Your Vault Key_ prompt:

![Warp command-line 'Save Your Vault Key' prompt](../media/images/quickstart/vault_setup/vault_setup_copy_vault_key.png)

🛠️ Just as you did with the personal access token in Azure DevOps and GitHub, copy the vault key and save it in a safe place — preferably a password manager. You will need it to unlock the personal access tokens that were encrypted into the vault.

🛠️ After you have copied and saved the vault key, press the **Enter** or **Return** key to continue.

You’ll see the final message, which confirms that the vault has been set up and the personal access tokens have been encrypted into the `config/vault.age` file (`config\vault.age` on Windows):

![Warp command-line 'All done!' text](../media/images/quickstart/vault_setup/vault_setup_end_screen.png)

#### Check the Vault’s Contents

Now that you’ve set up the vault, you can check its contents to make sure that the personal access tokens were encrypted into it, and that you have the vault key to unlock them. This is an optional step, but it’s a good idea to verify that everything is in place before you proceed with the migration.

🛠️ Run the following command, which starts the Warp command-line application that inspects the contents of the vault:

```bash
gh warp vault check
```

You’ll be prompted to enter your vault key:

![Warp command-line 'Enter the vault encryption key' prompt](../media/images/quickstart/vault_check/vault_check_start.png)

🛠️ Paste the vault key into the text area...

![Warp command-line 'Enter the vault encryption key' prompt with obfuscated pasted-in vault key](../media/images/quickstart/vault_check/vault_check_paste_key.png)

🛠️ ...then press the **Enter** or **Return** key to continue.

If you entered the correct vault key, you’ll see the contents of the vault:

![Warp command-line vault check results text](../media/images/quickstart/vault_check/vault_check_end_screen.png)

#### Store the Vault key in _Migration HQ_

Now that you’ve set up the vault and verified that it contains personal access tokens for both Azure DevOps and GitHub, you need to store the vault key in the _Migration HQ_ repository. This will allow the Warp GitHub Actions to access the personal access tokens you encrypted into the vault, which in turn will allow them to migrate your repositories from Azure DevOps to GitHub.

You _could_ do this manually by copying the vault key and pasting it into the _Migration HQ_ repository’s _Secrets_ section. However, Warp provides a command-line application that will do this for you. Let’s use it.

🛠️ Run the following command, which starts the Warp command-line application that stores the vault key in the _Migration HQ_ repository:

```bash
gh warp vault place
```

You’ll be greeted with the following text:

![Warp command-line 'Install Runner Credentials Vault Master Key' prompt](../media/images/quickstart/vault_place/vault_place_start.png)

🛠️ Press the **Enter** or **Return** key to continue.

You’ll be prompted to enter your vault key:

![Warp command-line 'Decrypt Credentials Vault' prompt](../media/images/quickstart/vault_place/vault_place_paste_key.png)

🛠️ Paste the vault key into the text area...

![Warp command-line 'Decrypt Credentials Vault' prompt with obfuscated vault key pasted in](../media/images/quickstart/vault_place/vault_place_pasted_key.png)

🛠️ ...then press the **Enter** or **Return** key to continue.

The app will store your vault key into the _Migration HQ_ repository’s secrets and display this message:

![Warp command-line 'All done!' text](../media/images/quickstart/vault_place/vault_place_end_screen.png)

You should confirm that your vault key was successfully stored in _Migration HQ_ by checking the repository’s _Secrets_ section in GitHub:

![GitHub 'Settings' page for the 'Migration HQ' repository](../media/images/quickstart/vault_place/github_settings.png)

🛠️ Open a browser tab or window to the _Migration HQ_ repository in GitHub and click the **Settings** tab.

🛠️ In the menu on the left side of the page, select **Secrets and variables** to expand it, then select **Actions**.

You should see the _Actions secrets and variables_ page for _Migration HQ_ :

![GitHub 'Action secrets and variables' page for the 'Migration HQ' repository](../media/images/quickstart/vault_place/github_action_secrets_variables.png)

🛠️ Check the _Repository secrets_ section and confirm that it contains a secret named `PKFS_MASTER_KEY`.

If you see the `PKFS_MASTER_KEY` secret, you have successfully stored the vault key in _Migration HQ_. If not, you should run the `gh warp vault place` command again.

#### Push the Changes to the Repository

Now that the vault key is stored as a secret in the _Migration HQ_ repository, Warp can use it to unlock the personal access tokens for Azure DevOps and GitHub stored inside the vault file. It’s time to push the vault file to _Migration HQ_.

![GitHub Desktop app, with the changes to the local clone being added and committed](../media/images/quickstart/vault_place/git_add_and_commit.png)

🛠️ Add `config/vault.age` to the Git staging area and commit the changes. You can do this using GitHub Desktop, as shown in the screenshot above, or with command-line Git...

```bash
git add .
git commit -m "Add credentials"
```

![GitHub Desktop app, with the changes to the local clone being pushed](../media/images/quickstart/vault_place/git_push.png)

🛠️ ...then push the changes to GitHub. Once again, you can do this either with GitHub Desktop or with the command line:

```bash
git push origin main
```

### 5. Connect Azure DevOps

The next step is to connect your Azure DevOps account to Warp. This will allow Warp to access the repositories you want to migrate from Azure DevOps to GitHub.

![Warp 'Connect Your Sources' page](../media/images/quickstart/connect_ado/warp_verify_credentials_1.png)

🛠️ Go back to the Warp browser tab or window. Make sure that you’re on the _Connect Your Sources_ page shown above, then click the **Check Credentials** button near the lower right corner of the page.

The text in the _Verify Credentials_ section will change to “We’re checking your Vault’s credentials. This will take a moment...”:

![Warp Sign In page](../media/images/quickstart/connect_ado/warp_verify_credentials_2.png)

🛠️ While Warp is examing your vault, switch to the browser tab or window that you were using for the _Migration HQ_ repository in GitHub:

![Warp Sign In page](../media/images/quickstart/connect_ado/github_verify_credentials_1.png)

🛠️ Select the **Actions** tab. This will display the list of _Migration HQ_’s workflows.

If you switched to the GitHub browser tab or window and clicked the **Actions** tab quickly enough, you should see a workflow with a spinning yellow icon named **Warp Runner**. The yellow icon denotes that it is currently running. This workflow is using the vault key you stored in _Migration HQ_’s secrets to unlock the personal access tokens for Azure DevOps and GitHub.

![Warp Sign In page](../media/images/quickstart/connect_ado/github_verify_credentials_2.png)

🛠️ Wait until the spinning yellow icon is be replaced by a green checkmark. This means that the vault key was successfully used to unlock the personal access tokens for Azure DevOps and GitHub.

![Warp Sign In page](../media/images/quickstart/connect_ado/warp_verify_credentials_3.png)

🛠️ Switch back to the browser tab or window for Warp. You should see a section below _Verify Credentials_ titled _Your Vault_. It should contain two items:

* An item representing the Azure DevOps Organization containing the repositories you want to migrate, and
* An item representing the GitHub organization where you want to migrate the repositories.

If you don’t see these items, click your browser’s **Refresh** button.

🛠️ Click the **Next** button.

You’ll arrive at the _All Done!_ page, which marks the end of the process of configuring the project:

![Warp Sign In page](../media/images/quickstart/connect_ado/warp_review_and_complete.png)

🛠️ Let’s check the project’s status. Click the **Go to Dashboard** button.

#### Check the Project’s Status

The _Dashboard_ page shows the status of the project you just configured. It will display the following statistics:

* The number of repositories that Warp found in the Azure DevOps Organization,
* the number of repositories that have been migrated to GitHub,
* the average number of repositories that have been migrated per day, and
* the overall progress of the migration, expressed as a percentage:

![Warp Sign In page](../media/images/quickstart/connect_ado/warp_dashboard_initial.png)

🛠️ Let’s look at the project’s settings. Select **Settings** from the menu on the left side of the page.

This will take you to the _Settings_ page. It has the following sections:

* **Configuration:** Contains the shortened hash for commit for the vault. Click on this hash to see the contents of the vault file on GitHub.
* **Destination:** Shows the name of the organization where the repositories will be migrated. It contains a link to the organization’s _Migration HQ_ repository.
* **Sources & Credentials:** Shows the names and IDs of the Azure DevOps Organizations and GitHub Organizations that are connected to the project.

#### Scan your Azure DevOps Organization for Repositories

![Warp Sign In page](../media/images/quickstart/connect_ado/warp_settings_initial.png)

🛠️ Click the **Scan Sources** button near the top of the _Settings_ page.

🛠️ Switch to the browser tab or window for the _Migrations HQ_ repository and select the **Actions** tab:

![Warp Sign In page](../media/images/quickstart/connect_ado/github_warp_runner_start.png)

You should see a new workflow with a spinning yellow icon named **Warp Runner**. The yellow icon denotes that it is currently running. This workflow is scanning the Azure DevOps Organization for repositories.

🛠️ Wait for the **Warp Runner** workflow to start and finish. You’ll know it’s finished when the spinning yellow icon is replaced by a green checkmark.

![Warp Sign In page](../media/images/quickstart/connect_ado/github_warp_runner_end.png)

🛠️ Switch back to the browser tab or window for Warp and select **Dashboard** from the menu on the left side of the page:

![Warp Sign In page](../media/images/quickstart/connect_ado/warp_dashboard_after_scan.png)

You should see the updated statistics on the _Dashboard_ page. The number of repositories found in the Azure DevOps Organization should now be displayed.

If you don’t see a count of discovered Azure DevOps repositories, click your browser’s **Refresh** button.

### 6. Migrate a Repository

You’ve created a new project, generated personal access tokens for Azure DevOps and GitHub, set up the vault, stored the vault key in _Migration HQ_, connected your Azure DevOps account to Warp, and scanned the Azure DevOps Organization for repositories.

It’s finally time to migrate a repository from Azure DevOps to GitHub!

🛠️ Switch to the browser tab or window with _Migration HQ_ and select the **Issues** tab:

![The 'Issues' page for the 'Migration HQ' repository in GitHub](../media/images/quickstart/migrate/github_issues.png)

After scanning the Azure DevOps Organization, Warp created an issue in the _Migration HQ_ repository for each repository it found. These issues are used to manage the migration of repositories from Azure DevOps to GitHub.

🛠️ Click on the issue for the repository you want to migrate. In this example, we”re clicking on the issue named **TailwindTraders-Website**.

The page for the issue will appear:

![Warp Sign In page](../media/images/quickstart/migrate/github_issue_zoomed_out.png)

The body of the issue — the part that contains a description and other notes about the issue — contains information assembled by Warp about the corresponding repository. The comments section is where you enter commands to and get responses from Warp.

![Warp Sign In page](../media/images/quickstart/migrate/github_issue_zoomed_in_1.png)

If you take a closer look at the body, you’ll see that it’s divided into the following subsections:

![Warp Sign In page](../media/images/quickstart/migrate/github_issue_zoomed_in_2.png)

* **Migration Status:** This section shows the current status of the migration. Since the migration hasn’t started yet, its status is **not started**.
* **Tasks:** This section has a checklist of the tasks that need to be performed to migrate the repository. Warp will automatically check off the tasks as they are completed.

Scrolling farther down the body, you’ll see these subsections:

![Warp Sign In page](../media/images/quickstart/migrate/github_issue_zoomed_in_expanded.png)

* **About:** This lists basic information about the source repository, such as when its last commit was, how many commits it’s had in the past year, who its most active contributor was, and its size.
* **Source & Destination:** This provides links to the source and the destination repositories.
* **Inventory:** This shows information about the destination repository. Since the migration hasn’t started yet, this section simply says that the repository hasn”t been migrated yet.

It’s time to migrate!

🛠️ Scroll down the page to the comments section...

![Warp Sign In page](../media/images/quickstart/migrate/github_issue_migrate_command.png)

🛠️ ...and in the first comment, enter the following command:

```bash
/migrate
```

In moments, Warp will reply with a follow-up comment announcing that the migration has started:

![Warp Sign In page](../media/images/quickstart/migrate/github_issue_migrate_response_1.png)

Depending on how many migrations Warp is performing at the same time, the migration may take a few to several minutes to complete.

When the migration is complete, you’ll see a comment from Warp with a link to the destination repository:

![Warp Sign In page](../media/images/quickstart/migrate/github_issue_migrate_response_2.png)

🛠️ Click on the link to visit the newly-migrated repository.

You’ll see the repository’s page — _in GitHub!_ — with all of its files, branches, and commits:

![Warp Sign In page](../media/images/quickstart/migrate/github_heres_the_repository.png)

When you started, the GitHub organization had a single repository: _Migration HQ_.

🛠️ Click on the organization’s name (near the top left corner of the page), followed by the **Repositories** tab.

![Warp Sign In page](../media/images/quickstart/migrate/github_organization_repos.png)

You’ll see that the organization now has _two_ repositories: _Migration HQ_ and the repository you just migrated from Azure DevOps.

Let’s take a look at _Migration HQ_.

🛠️ Click on the _Migration HQ_ repository.

You’ll see that there are now only _four_ open issues — one less than before:

![Warp Sign In page](../media/images/quickstart/migrate/github_updated_issues_count.png)

🛠️ Click on the **Issues** tab.

You’ll see the open issues, which are the remaining repositories to be migrated:

![Warp Sign In page](../media/images/quickstart/migrate/github_updated_issues_page.png)

🛠️ Let’s look at the closed issues. Click on the **Closed** link.

![Warp Sign In page](../media/images/quickstart/migrate/github_closed_issues_page.png)

You’ll see the issue for the repository you just migrated.

🛠️ Switch to the browser tab or window you were using for Warp. You’ll see that the Dashboard shows that the count of migrated repositories has increased by one:

![Warp Sign In page](../media/images/quickstart/migrate/warp_dashboard_after_migration.png)

Congratulations! You’ve successfully migrated a repository from Azure DevOps to GitHub using Warp.
