---
description: Diagnose and fix failed migrations
---

# Migration Diagnosis

**When a migration fails, use the *Diagnose Migration* skill to classify the root cause and post a structured remediation plan as a comment on the issue so your team knows exactly what went wrong and what to do next.**

Migration failures can be opaque. A comment on a backlog issue might say "migration failed" and link to a runner log with hundreds of lines. The agent cuts through that noise by reading the evidence and surfacing only what matters.

## How to Use It

1. Open the backlog issue in Migration HQ for the repository whose migration has failed. 
2. Assign the issue to the **Packfiles Warp** agent with the instructions: *"Diagnose the migration failure."*

The agent categorizes the failure and posts a diagnosis comment directly on the issue.

## What the Diagnosis Contains

The agent posts a comment on the issue with:

* **Root cause** — a single sentence stating what went wrong
* **Remediation steps** — a numbered list of specific actions to resolve the issue, including any Warp Vault changes, slash commands, or source system changes needed
* **Retry instruction** — the exact comment to post on the issue to retry the migration once remediation is complete

For most failure categories, the retry instruction is simply `/migrate`.

{% hint style="warning" %}
The `too-big` label (applied by Warp when a repository exceeds 10 GB) is always addressed in the diagnosis, even if another failure category is the primary cause. Size issues are a hard blocker that must be resolved regardless of what else is failing.
{% endhint %}