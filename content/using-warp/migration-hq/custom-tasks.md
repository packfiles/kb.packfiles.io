---
description: Define reusable checklists that appear automatically on issues.
icon: list-check
---

# Custom Tasks

### Overview

Custom tasks let you define reusable checklists in `warp.yml` that Warp automatically injects into issue descriptions. Tasks can target specific issues by label, or appear on every issue in your project.

Custom tasks are configured in your project's `warp.yml` file. For general information about `warp.yml`, see [Warp.yml](warp.yml.md).

### Configuration

Each custom task is defined under the `custom_tasks` block in `warp.yml`. A task entry requires:

* A **unique identifier** (the YAML key) — used internally to reference the task
* `title` — the display heading that appears in the issue body
* `body` — the task content, supporting full Markdown including checklists
* `labels` (optional) — an array of label names that control when this task appears

```yaml
custom_tasks:
  my_task_id:            # unique identifier
    title: "My Task"     # display heading
    body: |              # supports Markdown
      - [ ] Step one
      - [ ] Step two
    labels: ["my-label"] # optional — omit for global tasks
```

### Label-Specific Tasks

When a task includes a `labels` array, it only appears on issues that have at least one of those labels assigned. Label matching is case-insensitive.

```yaml
custom_tasks:
  migration_kickoff:
    title: "Migration Kickoff Checklist"
    body: |
      - [ ] Schedule kickoff meeting with stakeholders
      - [ ] Review source repository structure
      - [ ] Identify dependencies and blockers
      - [ ] Create migration timeline
    labels: ["migration", "kickoff"]
```

In this example, the checklist appears when either the `migration` or `kickoff` label is added to an issue.

### Global Tasks

Tasks defined without a `labels` key appear on every issue in the project. These are useful for checklists that apply universally, such as compliance or security reviews.

```yaml
custom_tasks:
  security_review:
    title: "Security Review"
    body: |
      - [ ] Review code for security vulnerabilities
      - [ ] Check for exposed credentials
      - [ ] Validate input sanitization
```

### Dynamic Injection

Warp automatically manages custom task content in issue descriptions:

1. **Adding a label** — When you add a label to an issue that matches a custom task's `labels` configuration, Warp updates the issue body to include the matching task content.
2. **Removing a label** — When you remove a label, Warp removes the corresponding task content from the issue body.

Custom tasks appear in the issue body under a **Tasks From Your Organization** heading, with each task rendered as a checkbox item.

> **Important:** Warp manages the issue body automatically. If you manually edit the issue description, your changes may be overwritten the next time labels are added to or removed from that issue. This ensures that custom task content stays synchronized with the issue's labels.

### Multiple Tasks Example

You can define multiple tasks with different label triggers. This example combines label-specific and global tasks:

```yaml
custom_tasks:
  frontend_checklist:
    title: "Frontend Development"
    body: |
      - [ ] Implement responsive design
      - [ ] Test across browsers
      - [ ] Optimize performance
    labels: ["frontend", "ui"]

  backend_checklist:
    title: "Backend Development"
    body: |
      - [ ] Design API endpoints
      - [ ] Implement data validation
      - [ ] Write unit tests
    labels: ["backend", "api"]

  compliance_review:
    title: "Compliance Review"
    body: |
      - [ ] Verify licensing requirements
      - [ ] Check data handling policies
    # No labels — appears on all issues
```
