# /rename-destination

## Description

Changes the name of the destination GitHub repository

[View in Knowledge Base](https://kb.packfiles.io/warp/commands/backlog-entry/rename-destination)

## Examples

### With Named Arguments:

```
/rename-destination --new-name <new-name>
```

### With Positional Arguments:

```
/rename-destination <new-name> 
```

## Arguments

### --new-name (Required)

* The new name of the destination GitHub repository.

**Value:**

* A name to use for the GitHub repository. Special characters will be converted to conform to GitHub's requirements.
* The specified repository name must be available in this GitHub organization.

## Authorization

* Not required.
