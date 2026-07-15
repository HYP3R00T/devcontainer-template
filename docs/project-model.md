---
icon: lucide/boxes
---

# The project model

A sustainable project separates decisions along two dimensions.

| | Project-agnostic | Project-specific |
| --- | --- | --- |
| **Hard constraints** | Portable checks such as valid configuration, clean text files, and protected branches | Language tests, type checks, security policies, and deployment requirements |
| **Soft constraints** | Small changes, understandable code, issue-driven work, and human accountability | Architecture, domain terminology, compatibility promises, and product priorities |

## Project-agnostic foundation

The template provides the smallest useful baseline shared by many projects: a reference environment, tool management, repository hygiene, Git hooks, contribution guidance, and CI integration. These mechanisms should remain useful when the eventual project uses Python, JavaScript, Rust, or several languages together.

## Project-specific layer

A real project must deliberately add its runtime, architecture, testing strategy, ownership boundaries, release policy, and operational requirements. The template cannot safely guess these decisions. Empty placeholders and speculative configuration create maintenance work without providing protection.

## Constraint does not mean documentation

A written rule is not automatically enforced. If a requirement can be checked deterministically and a failure must block integration, encode it in automation. If it requires context or judgment, state it clearly and review it consciously.

The objective is not maximum enforcement. It is to put each decision in the layer capable of maintaining it.
