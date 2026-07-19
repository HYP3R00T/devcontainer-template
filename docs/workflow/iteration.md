---
icon: lucide/refresh-cw
---

# Iterative development

!!! note "Pain point"

    Large batches of work are difficult to understand, verify, review, and reverse. When implementation silently
    expands beyond its accepted scope, traceability no longer explains what the pull request was meant to achieve.

The same loop applies to features, defects, refactoring, and documentation changes. The amount of explanation and
verification should match the risk, but the movement from accepted intent to reviewed evidence remains the same.

## Before coding

Confirm that the issue states the current problem, desired outcome, acceptance criteria, important exclusions, and
known dependencies. Create one branch for that issue so its work can be reviewed, abandoned, or integrated without
entangling unrelated changes.

One branch may occasionally address multiple issues when they describe one inseparable outcome, but that should be
the exception. Link every included issue and explain why separate pull requests would create a false boundary.

## During implementation

Make the smallest coherent change that satisfies the issue. Run fast checks frequently. Prefer direct readable
code over abstractions justified only by hypothetical reuse.

Commits should preserve meaningful implementation steps, not every experiment or save point. They can be revised
before review when doing so makes the history easier to understand. Whether the pull request is merged normally or
squashed is a repository choice; review quality depends on the complete pull-request diff, not on maximizing or
minimizing the number of commits.

A bug fix should reproduce the defect where practical, correct its cause, and add protection against recurrence. A
refactor should preserve behavior and explain the maintenance problem it removes. Documentation work should verify
both the source and the rendered output when presentation or navigation can change.

If implementation reveals a materially different problem, pause and update or split the issue before expanding the
change. Discovery is expected; silently changing the agreement is what damages traceability.

## Before integration

Open a pull request linking the issue. Explain what changed, how it was verified, and any risk or follow-up work. Review the complete diff as if another person wrote it. The quality gate must pass, but a passing gate does not replace review.

Merge only when the change is understandable, scoped, verified, and safe for the main branch. A solo maintainer
cannot provide independent approval, but can still review after a deliberate pause, inspect the rendered result,
and require the same recorded evidence. Create separate issues for valid follow-up work instead of silently
expanding the pull request.
