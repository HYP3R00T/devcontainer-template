# AGENTS.md

Instructions for coding agents working in this repository.

## Project overview

- Repo: `HYP3R00T/devcontainer-template` — a minimal, reusable devcontainer template.

## Environment setup

```sh
mise install
uv sync
prek install --hook-type pre-commit --overwrite
prek install --hook-type commit-msg --overwrite
```

Dev container runs `scripts/setup.sh` automatically on create.

## Expectations

- **Commits:** use conventional commits (`cz commit` if available); PRs should include a short summary of commands run.
- **Secrets:** never commit credentials; `.env` is gitignored and local-only.

## Agent behavior

- Prefer minimal diffs; don't refactor unrelated files.
- If tools are missing, run `mise install` before trying workarounds.
- Keep CI workflows and local guidance in sync when changing related behavior.
