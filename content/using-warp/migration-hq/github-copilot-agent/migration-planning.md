---
description: Plan your migration waves and generate a strategy document
---

# Migration Planning

**The *Migration Planning* skill reads every open backlog issue in your *Migration HQ*, scores each repository, assigns it to a migration wave, applies wave labels to the issues, and produces a migration strategy document all in a single step from the *Agents* tab.**

If you're starting a migration and need to understand the scope, sequence, and timeline of the work ahead, this is where to begin.

## How to Use It

1. Navigate to the **Agents** tab in your *Migration HQ* repository.
2. Select **Packfiles Warp** from the dropdown list of available agents.
3. Type a request such as: *"Plan my migration."*

The agent reads all open backlog issues, scores each repository, and delivers a complete strategy document with wave assignments for each repository (typically completes within a few minutes, depending on the size of your backlog).

{% hint style="info" %}
The agent reads from your existing backlog issues. Make sure you have scanned your sources and that repositories appear as open issues in *Migration HQ* before running planning.
{% endhint %}

## What the Agent Analyzes

For each backlog issue, the agent reads:

* **Repository size**
* **Commit activity**
* **Pull request count**
* **Pipeline count** — Azure DevOps only
* **Source platform**
* **Organization and team**
* **Size flags** — from the `too-big` label (repository exceeds 10 GB)

No CSV files or external data sources are required. The agent works entirely from the information already in your backlog.

## How Repositories Are Scored

Each repository receives a **Migration Compatibility Score** from 0 to 11, made up of three components:

**Size Score (0–5 points)**

| Repository Size | Points |
|---|---|
| Less than 10 MB | 5 |
| 10 MB – 100 MB | 4 |
| 100 MB – 500 MB | 3 |
| 500 MB – 5 GB | 2 |
| 5 GB – 40 GB | 1 |
| 40 GB or larger | 0 — exceeds Warp's size limit |

**Activity Score (0–3 points)**, based on commits in the past year:

| Commit Activity | Points |
|---|---|
| 0 commits | 3 |
| 1–10 commits | 2 |
| 11–100 commits | 1 |
| More than 100 commits | 0 |

**Simplicity Score (0–3 points)**, based on pull request count. For Azure DevOps repositories, pipeline count is also considered:

| Condition | Points |
|---|---|
| 0 PRs (and ≤ 1 pipeline for ADO) | 3 |
| ≤ 10 PRs (and ≤ 3 pipelines for ADO) | 2 |
| ≤ 50 PRs (and ≤ 10 pipelines for ADO) | 1 |
| More than 50 PRs (or more than 10 pipelines for ADO) | 0 |

{% hint style="info" %}
Bitbucket Server repositories are scored on pull request count only — Bitbucket Server does not have pipelines managed through Warp.
{% endhint %}

## Migration Waves

Based on the total score, each repository is assigned to one of four migration waves:

| Wave | Score | Risk Level | Description |
|---|---|---|---|
| Wave 1 | 9–11 | Low Risk | Small, inactive or low-activity, simple repositories |
| Wave 2 | 6–8 | Medium Risk | Standard repositories with moderate complexity |
| Wave 3 | 3–5 | High Risk | Larger or more complex repositories requiring planning |
| Manual Review | 0–2 | Very High Risk | Requires individual assessment before migration |

**Override conditions** — regardless of score, a repository is placed in Manual Review if:
* Its size is 40 GB or larger (exceeds Warp's absolute size limit)
* It has more than 10 pipelines (Azure DevOps only)

## Wave Labels

After computing wave assignments, the agent automatically applies a `planning:wave-N` label to each backlog issue. These labels appear in the *Migration HQ* issue list and can be used to filter issues by wave.

| Wave | Label |
|---|---|
| Wave 1 | `planning:wave-1` |
| Wave 2 | `planning:wave-2` |
| Wave 3 | `planning:wave-3` |
| Manual Review | `planning:manual-review` |

## The Migration Strategy Document

The agent produces a markdown document covering:

1. **Executive Summary** — total repositories, wave distribution, and estimated duration
2. **Repository Inventory Overview** — breakdown by organization, project, and size band
3. **Repository Scoring and Wave Assignment** — scoring methodology and wave summary tables
4. **Migration Wave Strategy** — per-wave details and timeline
5. **Repository Size Analysis** — top 10 largest repositories and size risk assessment
6. **Warp Limitations and Considerations** — what data is and is not migrated
7. **Risk Assessment** — a risk register derived from your actual inventory
8. **Pre-Migration Checklist** — actionable setup steps
9. **Post-Migration Actions** — slash command reference for your source platform
10. **Licensing and Capacity Planning** — capacity recommendation based on your repository count
11. **Key Resources** — links to documentation, support, etc

If your migration includes both Azure DevOps and Bitbucket Server repositories, the document presents a combined view with provider-specific sections where the two platforms differ.