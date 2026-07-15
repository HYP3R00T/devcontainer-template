---
icon: lucide/lock-keyhole
---

# Hard constraints

A hard constraint has an objective result and a mechanism capable of stopping an invalid change.

## Enforcement layers

| Layer | Role | Important limitation |
| --- | --- | --- |
| Editor configuration | Prevent mistakes while writing | Contributors can disable or bypass it |
| Git hooks | Provide fast feedback before a commit completes | Local hooks can be skipped |
| Continuous integration | Reproduce checks on a clean runner | It blocks only when required by repository rules |
| GitHub rulesets | Protect branches and require successful checks | Repository administrators must configure them |

This template uses EditorConfig and Git attributes for consistent text, `prek` for Git lifecycle checks, and a quality-gate workflow that runs the same hook suite in GitHub Actions.

## What belongs here

Good hard constraints are deterministic, reasonably fast, stable, and accompanied by a useful failure message. Syntax validation, formatting, static analysis, tests, generated-file checks, and forbidden secret patterns are common examples.

Do not automate a subjective preference merely to call it enforcement. A brittle check creates noise, teaches contributors to bypass the gate, and makes legitimate work harder.
