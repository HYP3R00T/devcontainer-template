---
icon: lucide/library
---

# Hook providers

The configuration uses remote hook repositories. Each provider owns one or more hooks and supplies the executable environment that `prek` runs.

| Provider | Role in this template | Configured hooks |
| --- | --- | --- |
| [pre-commit-hooks](pre-commit-hooks.md) | Generic file, portability, hygiene, and repository-safety checks | 15 |
| [rumdl-pre-commit](rumdl-pre-commit.md) | Markdown validation | 1 |
| [Commitizen](commitizen.md) | Commit-message validation | 1 |
| [shellcheck-py](shellcheck-py.md) | Shell static analysis | 1 |

Open a provider page to see its official source first, followed by the hooks selected from it, why they are present, and what to do when they fail. The committed `.pre-commit-config.yaml` remains the source of truth for exact revisions and options.
