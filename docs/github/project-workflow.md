---
icon: lucide/kanban
---

# Configure the issue workflow Project

!!! note "Pain point"

    Repository templates copy files, not account- or organization-owned GitHub Projects. The issue skills cannot
    safely infer lifecycle state unless each derived repository has one unambiguous Project with the expected
    workflow.

The project-level `refine-issue` and `issue-to-pr` skills use live GitHub Project state as their handoff boundary.
Configure a separate Project for a derived repository when trusted maintainers will use those skills or when the
issue queue needs explicit readiness and delivery state.

A Project is optional. The skills stop without mutation when no suitable Project exists, more than one Project is
ambiguous, or the authenticated account cannot read or update it.

## Create the Project

Create an account- or organization-owned Project from GitHub's **Projects** page. Give it the derived project's
name, link it to the repository, and decide whether its visibility matches the contributor workflow. A private
Project is suitable for a private maintainer queue, but contributors and agents without access cannot use the
lifecycle skills.

Configure the built-in `Status` field with these options in this order:

1. `Backlog`
2. `Ready`
3. `In Progress`
4. `In Review`
5. `Blocked`
6. `Done`

These states have distinct meanings:

| Status | Meaning |
| --- | --- |
| `Backlog` | Proposed work that has not passed the readiness standard |
| `Ready` | One accepted, cohesive outcome with complete implementation guidance |
| `In Progress` | A trusted delivery workflow has claimed the issue |
| `In Review` | The latest pull-request head is published, verified, and awaiting human review |
| `Blocked` | Delivery started but now requires a material decision or unavailable dependency |
| `Done` | The issue is closed after its outcome was integrated or otherwise finalized |

Optionally add a single-select `Priority` field with `P0`, `P1`, `P2`, and `P3`. Priority helps order accepted work
but is not required by either skill and must not be treated as lifecycle state.

## Configure built-in automation

Enable the smallest useful set of Project workflows:

1. **Auto-add to project:** add issues from the one derived repository. Restrict the filter to issues so pull
   requests do not become duplicate lifecycle items.
2. **Item added to project:** set newly added items to `Backlog`.
3. **Item closed:** set closed items to `Done`.
4. **Auto-add sub-issues to project:** enable only if the project uses parent and sub-issues.

Use a closing keyword such as `Closes #123` in a pull request only when that pull request completely resolves the
issue. GitHub closes the issue after merge, and the item-closed workflow then moves its Project item to `Done`.
Keep merge a human action; Project automation must not bypass the repository ruleset or required checks.

Do not automate `Ready`, `In Progress`, or `In Review`. Those transitions represent verified handoffs:

- `refine-issue` owns `Backlog → Ready`;
- `issue-to-pr` owns `Ready → In Progress → In Review`; and
- a maintainer or separately authorized finalization process owns exceptional `Blocked` or post-merge correction.

## Prepare GitHub CLI access

The skills require GitHub CLI authentication with repository and Project access. Check the active account without
printing its token:

```bash
gh auth status
gh auth refresh -s project
gh project list --owner OWNER
gh project field-list PROJECT_NUMBER --owner OWNER
```

For an organization-owned Project, use the organization login as `OWNER`. Confirm that exactly one Project attached
to an issue exposes the lifecycle above. Do not commit Project, field, item, or option IDs: the skills discover live
identifiers and keep them only for the active invocation.

## Verify the lifecycle

Create a disposable issue and confirm that:

1. GitHub adds it to the intended Project as `Backlog`.
2. No second Project creates an ambiguous matching lifecycle.
3. Closing the issue changes its Project status to `Done`.
4. Reopening or exceptional closure behavior matches the project's documented policy.

Then remove or close the disposable issue according to the project's normal maintenance policy. A saved Project
configuration is not sufficient proof; verify the observed issue timeline and final field value.

## Template boundary

Creating a repository from this template does not copy this Project, its workflows, its visibility, or repository
links. Configure and verify those hosted settings separately for every derived repository. The same applies to the
[default-branch ruleset](protect-main.md).
