# /integrate-boards

## Description

Configures an integration between Azure Boards and the destination GitHub repository.

[View in Knowledge Base](https://kb.packfiles.io/using-warp/slash-commands/azure-devops/integrate-boards)

{% hint style="warning" %}
ADO now rejects GitHub Personal Access Tokens (PAT) with any extra scopes during ADO Boards integration. The GitHub destination PAT (which needs broad scopes) is fundamentally incompatible with the `integrate-boards` command.

A possible workaround:

1. Create or use an existing GitHub App connection in ADO (Project Settings > GitHub Connections), created via the OAuth flow.
2. Call the [ADO Boards GitHub Connections API](https://learn.microsoft.com/en-us/rest/api/azure/devops/wit/github-connections/update?view=azure-devops-rest-7.2&tabs=HTTP) update endpoint directly to add the repo using a POST request to:

`https://dev.azure.com/{org}/{project}/_apis/githubconnections/{connectionId}/repos?api-version=7.1-preview.1`

**Key details**:
- You cannot send plain strings.
- `gitHubRepositoryUrls` in the [request body](https://learn.microsoft.com/en-us/rest/api/azure/devops/wit/github-connections/update?view=azure-devops-rest-7.2&tabs=HTTP#request-body) **must** be an array of objects (each with a `gitHubRepositoryUrl` property) and `operationType` must be `add`.

```json
{
  "gitHubRepositoryUrls": [
    {
      "gitHubRepositoryUrl": "https://github.com/test-account/repo1"
    },
    {
      "gitHubRepositoryUrl": "https://github.com/test-account/repo2"
    },
    {
      "gitHubRepositoryUrl": "https://github.com/test-account/repo3"
    },
    {
      "gitHubRepositoryUrl": "https://github.com/test-account/repo399"
    }
  ],
  "operationType": "add"
}
```

See this [Sample Request](https://learn.microsoft.com/en-us/rest/api/azure/devops/wit/github-connections/update?view=azure-devops-rest-7.2&tabs=HTTP#add-list-of-repos-to-the-specified-github-connection)

{% endhint %}

## Example

```
/integrate-boards
```

## Authorization

* Not required.
