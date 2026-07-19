---
icon: lucide/shield-check
---

# Hard and soft constraints

!!! note "Pain point"

    Projects often treat every rule as either optional prose or mandatory automation. Some requirements are then
    easy to bypass, while subjective preferences become brittle checks that block valid work.

Constraints keep development inside an agreed boundary, but their enforcement must match the kind of decision they
represent.

| Kind | Meaning | Examples |
| --- | --- | --- |
| **Hard constraint** | A machine can evaluate it and stop an invalid operation | Parsing, formatting, tests, required CI checks |
| **Soft constraint** | A human or agent must interpret it in context | Scope, readability, architecture, adequate explanation |

Soft does not mean optional. A maintainer can reject a pull request that violates a review standard. It means the
decision cannot be reduced safely to a deterministic check.

## Enforcement layers

| Layer | Role | Important limitation |
| --- | --- | --- |
| Editor configuration | Prevent mistakes while writing | Contributors can disable or bypass it |
| Git hooks | Provide fast feedback around Git operations | Local hooks can be skipped |
| Continuous integration | Reproduce checks on a clean runner | It blocks merging only when GitHub requires the result |
| GitHub rulesets | Protect integration points and require successful checks | Repository administrators must configure them |
| Review | Evaluate scope, design, clarity, and evidence | Judgment must be explained and applied consistently |

This template uses EditorConfig and Git attributes for consistent files, `prek` for local Git automation, a Quality
Gate workflow for clean-runner verification, and a documented ruleset for default-branch integration.

## Soft constraints in this template

Contribution guidance, issue forms, pull-request prompts, and review uphold expectations such as:

- understand and be able to explain everything submitted;
- keep a change focused on its accepted issue;
- prefer the smallest complete solution;
- avoid speculative abstractions and unrelated refactoring;
- document behavior that users or maintainers must know; and
- stop when implementation requires a material change in scope.

AI-assisted work follows the same standard. The contributor owns the result and must be able to maintain it without
the generating tool.

## Choose enforcement deliberately

Automate a requirement when its result is objective, stable, reasonably fast, and important enough to block work.
Keep contextual judgment in review. Avoid implementing the same rule independently at several layers; one shared
command used locally and in CI is easier to understand and maintain.
