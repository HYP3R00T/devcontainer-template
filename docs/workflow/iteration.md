---
icon: lucide/refresh-cw
---

# Iterative development

The same loop applies to features, defects, refactoring, and documentation changes.

## Before coding

Confirm that the issue states the current problem, desired outcome, acceptance criteria, important exclusions, and known dependencies. If implementation reveals a materially different problem, update or split the issue before expanding the change.

## During implementation

Create a dedicated branch and make the smallest coherent change that satisfies the issue. Run fast checks frequently. Prefer direct readable code over abstractions justified only by hypothetical reuse.

A bug fix should reproduce the defect where practical, correct its cause, and add protection against recurrence. A refactor should preserve behavior and explain the maintenance problem it removes.

## Before integration

Open a pull request linking the issue. Explain what changed, how it was verified, and any risk or follow-up work. Review the complete diff as if another person wrote it. The quality gate must pass, but a passing gate does not replace review.

Merge only when the change is understandable, scoped, verified, and safe for the main branch. Create separate issues for valid follow-up work instead of silently expanding the pull request.
