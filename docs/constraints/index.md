---
icon: lucide/shield-check
---

# Constraints

Constraints keep development inside an agreed boundary. Their strength depends on where they are implemented.

## Hard and soft constraints

| Kind | Meaning | Examples |
| --- | --- | --- |
| [Hard](hard.md) | A machine can evaluate it and block progress when it fails | Parsing, formatting, tests, required CI checks |
| [Soft](soft.md) | A human or agent must interpret it in context | Scope, readability, architecture, adequate explanation |

Soft does not mean optional. A pull request can be rejected for violating a review standard. It means the decision cannot be reduced safely to a deterministic check.

## Place rules at the correct layer

Use editor settings for immediate guidance, Git hooks for fast local feedback, CI for authoritative reproducible checks, GitHub rulesets for integration policy, and review for contextual judgment. Avoid implementing the same requirement independently in several places; expose one command that local tools and CI can both run where practical.
