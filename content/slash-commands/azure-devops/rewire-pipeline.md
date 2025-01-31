## /rewire-pipeline
### Description
Rewires an Azure DevOps Pipeline


[View in Knowledge Base](https://kb.packfiles.io/warp/commands/azure-devops/rewire-pipeline)



### Examples

#### With Named Arguments:
```
/rewire-pipeline --id <id> [--again]
```
#### With Positional Arguments:
```
/rewire-pipeline <id> [--again]
```
### Arguments





#### --id (Required)

- The ID of the pipeline to rewire. This ID is shown in the Azure Pipelines table under the "Inventory" section of the Backlog Entry.

**Value:**
  - Must be an integer number.
  - The requested pipeline ID must match an ID shown in the Azure Pipelines table under the "Inventory" section of the Backlog Entry.






#### --again (Optional)

- When provided, the rewiring step will be performed again even if the pipeline has been rewired previously.

**Value:**
  - None (boolean flag).


### Authorization

- Not required.