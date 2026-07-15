---
icon: lucide/log-in
---

# Project-entry automation

The enter hook handles small setup actions that should be true whenever work begins.

## What it does

1. Finds the repository root.
2. Installs Commitizen with `uv tool install commitizen` when `uv` exists and `cz` does not.
3. Installs the `prek` pre-commit hook when missing.
4. Installs the `prek` commit-message hook when missing.

The checks make repeated entry safe. Existing valid hooks and tools are left alone.

## Platform implementations

- Linux, macOS, and the dev container use `scripts/enter_project.sh`.
- Native Windows uses `scripts/enter_project.ps1`.

The scripts intentionally have the same behavior. Any functional change must be made to both and syntax-checked on both platforms.

## Why this is a hook

Tool versions belong in Mise, but Git-hook installation changes repository-local state. The enter hook is an appropriate boundary because it verifies that state without placing generated Git-hook files under version control.

Keep entry automation short. Slow builds, tests, network-heavy updates, and destructive actions do not belong here.

## Official documentation

- [Mise hooks](https://mise.jdx.dev/hooks.html)
- [uv tool commands](https://docs.astral.sh/uv/guides/tools/)
- [prek documentation](https://prek.j178.dev/)
- [Commitizen documentation](https://commitizen-tools.github.io/commitizen/)
- [Conventional Commits specification](https://www.conventionalcommits.org/)
