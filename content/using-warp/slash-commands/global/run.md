# /run

## Description

Executes a custom script defined in your project's `warp.yml` configuration file. Scripts run on a GitHub Actions runner agent and results are posted as a comment on the issue.

[View in Knowledge Base](https://kb.packfiles.io/using-warp/slash-commands/global/run)

## Examples

### Basic (no arguments):

```
/run notify_team
```

### With Arguments:

```
/run update_wiki --script_args wiki_page=migrations status=in_progress owner=chaserx
```

### With Boolean Flags:

```
/run cleanup --script_args target=logs dry_run
```

## Arguments

### script_id (Required)

* The identifier of the script to run, as defined in your project's `warp.yml` configuration under the `scripts:` key.

**Value:**

* Must match a script identifier configured in `warp.yml`.

### --script_args (Optional)

* Arguments to pass to the script. Provide space-separated `key=value` pairs after the `--script_args` flag. Boolean flags (without a value) are set to `"true"`.

**Value:**

* Space-separated `key=value` pairs.
* Arguments must match those defined in the script's `arguments` configuration in `warp.yml`. Unknown arguments are rejected.
* Required arguments (as configured in `warp.yml`) must be provided.

## Authorization

* When script policies are configured in `warp.yml` under `policies.scripts`, only the listed users and teams can execute the script.
* When no script policies are defined, authorization is not required.

See [Custom Scripts](../../migration-hq/custom-scripts.md) for configuration details.
