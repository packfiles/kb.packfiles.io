---
icon: scroll
---

# Using Credentials in Scripts

Warp Vault provides a simple Query Language (VaultQL) that allows you to search for and extract specific credential provider configurations stored in your vault. This feature helps you extract any properties you might need in scripts or other parts of your workflow.

Using the [Warp CLI](../../../warp-cli.md) command `gh warp vault query`, you can supply a query to locate one or more credentials and optionally retrieve only a specific property or nested value.

{% hint style="success" %}
Schemas for each credential provider type are documented in the [Vault Schema](vault-schema/) section. Refer to these when writing queries or parsing their results.
{% endhint %}

### Quick Example

The following example demonstrates how VaultQL can be used in a shell scripting scenario. Credentials are queried from Warp Vault and passed into GitHub Enterprise Importer.

```
export PKFS_MASTER_KEY="AGE-SECRET-KEY-..."

export BBS_USERNAME=`gh warp vault get '(type:bitbucketserver).credentials.username'`
export BBS_PASSWORD=`gh warp vault get '(type:bitbucketserver).credentials.password'`
export BBS_URL=`gh warp vault get '(type:bitbucketserver).url'`

gh bbs2gh inventory-report --bbs-server-url $BBS_URL --bbs-username $BBS_USERNAME --bbs-password $BBS_PASSWORD --verbose
```

### Query Syntax

A query is specified at the beginning of the command and must be enclosed in parentheses. An optional extraction path (to pull out a specific property) is appended immediately after the closing parenthesis.

### General Format

```
gh warp vault get '(QUERY ELEMENTS)'[.EXTRACTION_PATH]
```

* Query Elements: A comma-separated list of key/value pairs used to match provider properties.
* Extraction Path: A dot-prefixed path indicating which property to return from the matched provider.

Both query elements and extraction paths are case-insensitive.

### Query Elements

Each element in the query helps narrow down your search. There are two types of elements:

#### Top-Level Properties

These match properties at the root level of a provider’s JSON.

**Supported Keys**

The `type` and `uuid` keys are always available.

**Syntax Example:**

Searches for a provider with the specified UUID:

`(uuid:C3AA88A0-0B1A-4567-B45F-6DB024F15FDE)`

Searches for providers of type `GitHubDestination`:

`(type:GitHubDestination)`

#### Data Path Elements

These match properties within the provider’s "data" field. When using these in a query, begin the element with a period (`.`).

**Syntax Example**

Matches a provider whose data contains the key `organization_slug` with the value `your-github-org-slug`:

`(.organization_slug:"your-github-org-slug")`

#### Optional Elements

You can use the `?` prefix to mark a query element as optional. This helps refine the search when some properties might not be available on every provider.

**Syntax Example**

The following query indicates that while it’s preferable for the returned provider to have an `organization_slug` of `org3`, it isn’t mandatory for the match:

`(?.organization_slug:"org3")`

Multiple elements are separated by commas. All non-optional elements must match for a provider to be considered, while optional elements contribute to a "best match" ranking if several providers qualify.

#### Extraction Paths

After the closing parenthesis of your query, you can specify an extraction path to return just one property instead of the entire provider JSON.

**Syntax Example**

Returns the value of `organization_slug` from the matching provider:

```
gh warp vault get '(uuid:C3AA88A0-0B1A-4567-B45F-6DB024F15FDE).organization_slug'
```

**Syntax Example - Nested Properties**

Retrieves the nested `password` field inside the credentials object of a Bitbucket Server provider:

```
gh warp vault get '(type:BitbucketServer).credentials.password'
```

### Examples

**Full Provider Retrieval**

Returns the complete JSON object for the provider with the specified UUID:

```
gh warp vault get '(uuid:C3AA88A0-0B1A-4567-B45F-6DB024F15FDE)'
```

**Specific Property Extraction**

Returns only the organization slug from the matched provider:

```
gh warp vault get '(uuid:C3AA88A0-0B1A-4567-B45F-6DB024F15FDE).organization_slug'
```

**Nested Property Extraction**

Returns the nested password value (e.g., "bbs-password") from within the provider’s credentials:

```
gh warp vault get '(uuid:474F6208-B195-4CE4-AFA7-80CF182A43BC).credentials.password'
```

**Using Optional Elements for Flexible Matching**

```
gh warp vault get '(type:DemoProvider,?.organization_slug:"org3",?.access_scope:"global").pat'
```

**Query**

**Mandatory**

* `type:DemoProvider`
  * Only providers of type `DemoProvider` are considered.

**Optional**

* `?.organization_slug:"org3"`
  * Prefers a provider with an organization slug of `org3`.
* `?.access_scope:"global"`
  * Alternatively, a provider with `global` `access_scope` is acceptable.

**Extraction**

* `.pat`
  * Returns only the personal access token from the matched provider.

**Return Value**

The `pat` value of the provider that best matches the criteria.

**Strict Queries**

The following strict query requires a `DemoProvider` with an exact `organization_slug` of `org3`. If no provider meets all criteria, nothing is returned (and an error is reported).

```
gh warp vault get '(type:DemoProvider,.organization_slug:"org3").pat'
```

**Matching Behavior & Tips**

**Mandatory vs. Optional**\
Providers must match all mandatory (non-optional) elements. Optional elements help select the best match when multiple providers qualify.

**Case Sensitivity**\
Query keys and values are normalized (case-insensitive), so you can use uppercase or lowercase letters interchangeably.

**No Matches**\
If no provider meets the mandatory criteria, the command will return an error indicating that no provider matches the query.

**Extraction Fallback**\
If you omit an extraction path, the command returns the complete JSON of the best-matching provider.
