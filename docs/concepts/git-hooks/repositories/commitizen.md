---
icon: lucide/message-square-check
---

# Commitizen

Official source: [commitizen-tools/commitizen](https://github.com/commitizen-tools/commitizen)

The configured `commitizen` hook runs at the `commit-msg` stage. Unlike file hooks, it receives the temporary file containing the proposed commit message and validates that message before Git creates the commit.

## Why it is included

This repository follows [Conventional Commits](https://www.conventionalcommits.org/). Structured messages make history easier to scan and can later support release notes, changelogs, and semantic versioning without requiring those release features today.

## Failure and resolution

A failure means the final message does not follow the accepted convention. Rewrite it in this form:

```text
<type>[optional scope]: <description>
```

Use `cz commit` for an interactive prompt, or validate a message directly with `cz check --message`. The project-entry automation installs the `commit-msg` Git hook so ordinary `git commit` commands are validated automatically.

See Commitizen's official [automatic checking guide](https://commitizen-tools.github.io/commitizen/tutorials/auto_check/) and [commit command](https://commitizen-tools.github.io/commitizen/commands/commit/).
