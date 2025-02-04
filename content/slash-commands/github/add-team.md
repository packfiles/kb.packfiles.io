# /add-team

## Description

Adds a given team to the migrated repository in GitHub with the specified permissions.

[View in Knowledge Base](https://kb.packfiles.io/warp/commands/github/add-team)

## Examples

### With Named Arguments:

```
/add-team --team-name <team-name> --permission <permission>
```

### With Positional Arguments:

```
/add-team <team-name> <permission> 
```

## Arguments

### --team-name (Required)

* The slug of the team to add to the repository. Must be the name of a team in this GitHub organization.

**Value:**

### --permission (Optional)

* The permission to grant the team on the migrated repository. We accept the following permissions to be set: pull, triage, push, maintain, admin. You can also specify a custom repository role name, if this organization has defined any. If no permission is specified, the team's permission attribute will be used to determine what permission to grant the team on the migrated repository.

**Value:**

* Must be one of the following: pull, triage, push, maintain, admin.

## Authorization

* The user who invokes this command must be a GitHub organization administrator.
