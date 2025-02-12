---
icon: '5'
---

# Scan for Source Repositories

{% include "../../.gitbook/includes/search-for-the-emoji-if....md" %}



### Verify Your Credentials

The next step is to connect your Azure DevOps account to Warp. This will allow Warp to access the repositories you want to migrate from Azure DevOps to GitHub.

![Warp’s Connect Your Sources page.](../../media/images/quickstart/connect_ado/warp_verify_credentials_1.png)

🛠️ Go back to the Warp browser tab or window. Make sure that you’re on the _Connect Your Sources_ page shown above, then click the **Check Credentials** button near the lower right corner of the page.

The text in the _Verify Credentials_ section will change to “We’re checking your Vault’s credentials. This will take a moment...”:

![Warp’s Connect Your Sources page, after the Check Credentials button is clicked.](../../media/images/quickstart/connect_ado/warp_verify_credentials_2.png)

🛠️ While Warp is examining your vault, switch to the browser tab or window that you were using for the _Migration HQ_ repository in GitHub:

![The Actions page of Migration HQ, showing the runner agent verifying the vault credentials. ](../../media/images/quickstart/connect_ado/github_verify_credentials_1.png)

🛠️ Select the **Actions** tab. This will display the list of _Migration HQ_’s workflows.

If you switched to the GitHub browser tab or window and clicked the **Actions** tab quickly enough, you should see a workflow with a spinning yellow icon named **Warp Runner Agent**. The yellow icon denotes that it is currently running. This workflow is using the vault key you stored in _Migration HQ_’s secrets to unlock the personal access tokens for Azure DevOps and GitHub.

![The Actions page of Migration HQ, after the runner agent has completed its tasks.](../../media/images/quickstart/connect_ado/github_verify_credentials_2.png)

🛠️ Wait until the spinning yellow icon is be replaced by a green checkmark. This means that the vault key was successfully used to unlock the personal access tokens for Azure DevOps and GitHub.

🛠️ Switch back to the browser tab or window for Warp:

<figure><img src="../../media/images/quickstart/connect_ado/warp_verify_credentials_3.png" alt=""><figcaption><p>Warp’s <em>Connect Your Sources</em> page, after the vault credentials have been verified.</p></figcaption></figure>

You should see a section below _Verify Credentials_ titled _Your Vault_. It should contain two items:

* An item representing the Azure DevOps Organization containing the repositories you want to migrate, and
* An item representing the GitHub organization where you want to migrate the repositories.

If you don’t see these items, click your browser’s **Refresh** button.

🛠️ Click the **Next** button.

You’ll arrive at the _All Done!_ page, which marks the end of the process of configuring the project:

![Warp’s Review and Complete page.](../../media/images/quickstart/connect_ado/warp_review_and_complete.png)

### Check the Project’s Status

🛠️ Let’s check the project’s status. Click the **Go to Dashboard** button.

#### Check the Project’s Status

The _Dashboard_ page shows the status of the project you just configured:

<figure><img src="../../media/images/quickstart/connect_ado/warp_dashboard_initial.png" alt=""><figcaption><p>Warp’s <em>Dashboard</em> page.</p></figcaption></figure>

The **Trends** section displays the following statistics:

* The number of repositories that Warp found in the Azure DevOps Organization,
* the number of repositories that have been migrated to GitHub,
* the average number of repositories that have been migrated per day, and
* the overall progress of the migration, expressed as a percentage.

The text above the **Trends** section says “Tasks in Progress” and “Scanning your sources...” Warp is scanning your Azure DevOps organization for repositories. Let’s see this process in action.

🛠️ Switch to the browser tab or window for the _Migrations HQ_ repository and select the **Actions** tab:

![The Actions page of Migration HQ, showing the runner agent scanning the Azure DevOps organization for repositories. ](../../media/images/quickstart/connect_ado/github_warp_runner_start.png)

You should see a new workflow with a spinning yellow icon named **Warp Runner Agent**. The yellow icon denotes that it is currently running. This workflow is scanning the Azure DevOps organization for repositories.

🛠️ Wait for the Warp Runner Agent workflow to start and finish. You’ll know it’s finished when the spinning yellow icon is replaced by a green checkmark. The process may take a few minutes, depending on how many repositories are in your Azure DevOps organization.

![The Actions page of Migration HQ, after the runner agent has completed its tasks.](../../media/images/quickstart/connect_ado/github_warp_runner_end.png)

🛠️ When the Warp Runner Agent has finished its tasks, switch back to the browser tab or window with the Warp Dashboard:

![Warp’s Dashboard page, after the Azure DevOps organization has been scanned for repositories.](../../media/images/quickstart/connect_ado/warp_dashboard_after_scan.png)

You should see the updated statistics on the _Dashboard_ page. The number of repositories found in the Azure DevOps Organization should now be displayed.

If you don’t see a count of discovered Azure DevOps repositories, click your browser’s **Refresh** button.
