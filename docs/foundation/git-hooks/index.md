---
icon: lucide/git-commit-horizontal
---

# Git hooks with prek

!!! note "Pain point"

    Repeatable checks provide little protection when contributors must remember to run them manually. Mistakes are
    then discovered late in review or CI, after the feedback has become slower and more expensive to address.

`prek` manages automation at Git lifecycle events. A hook may inspect files, modify files, invoke project scripts, validate commit messages, or enforce repository policy.

## How to use this section

- Read [How hooks run](#how-hooks-run) to understand the execution model.
- Open a provider page to learn why its selected hooks exist and how to resolve failures.
- Use the commands in [Maintenance](#maintenance) to run or update the suite.

## How hooks run

A definition in `.pre-commit-config.yaml` connects four ideas:

- **Stage:** the Git event, such as `pre-commit` or `commit-msg`.
- **Entry:** the program or script to execute.
- **Input:** staged files, a commit-message file, or stage-specific data.
- **Environment:** an isolated hook environment or an existing system command.

This template installs `pre-commit` and `commit-msg` hooks. See the official [stage reference](https://prek.j178.dev/reference/configuration/#supported-git-hook-stages).

## Configured providers

The [hook providers](providers/index.md) section groups hooks by the repository or built-in source that supplies them. Each provider page begins with its official documentation and explains every selected hook in context.

| Provider | Responsibility |
| --- | --- |
| [pre-commit-hooks](providers/pre-commit-hooks.md) | Generic validity, portability, hygiene, and protection |
| [rumdl-pre-commit](providers/rumdl-pre-commit.md) | Markdown validation |
| [Commitizen](providers/commitizen.md) | Commit-message validation |
| [shellcheck-py](providers/shellcheck-py.md) | Shell static analysis |

## Running project scripts

A project can connect its own script or Mise task through a local hook:

```yaml
- repo: local
  hooks:
    - id: project-check
      name: Project check
      entry: mise run check
      language: system
      pass_filenames: false
      stages: [pre-commit]
```

This is an extension pattern, not a currently configured hook. Prefer a stable Mise task so contributors, Git hooks, agents, and CI call the same command. Keep pre-commit work fast; move slow comprehensive checks to CI or a later stage.

## Maintenance

```bash
prek run --all-files
prek update
prek run --all-files
```

Review `.pre-commit-config.yaml` after an update. The official [prek workflows](https://prek.j178.dev/usage/) document additional selection, debugging, cache, and installation commands.
