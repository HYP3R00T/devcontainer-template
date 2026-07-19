# AGENTS.md

Instructions for coding agents working in this repository.

## Commands

```sh
mise install
prek run --all-files
uvx zensical build --clean  # documentation changes
```

Run any additional tests or builds documented by the project.

## Approach

This is a minimal, language-agnostic Dev Container template. Do not introduce a
language, framework, service, or workflow until the adapted project chooses it.

Understand the request and trace the affected code before editing. Then use the
first option that fully satisfies the requirement:

1. Avoid building something that is not needed.
2. Reuse an existing repository pattern or capability.
3. Use the standard library or a native platform feature.
4. Use a suitable dependency that is already installed.
5. Add the minimum new code or configuration necessary.

Prefer the smallest complete, readable, and maintainable solution. Fix root
causes rather than symptoms. Avoid speculative abstractions, unnecessary files,
avoidable dependencies, unrelated refactoring, and cleverness without benefit.

Never trade away validation, error handling, security, accessibility, data
protection, compatibility, or relevant edge cases merely to reduce the diff.

## Verification

- Inspect existing changes before editing and preserve unrelated work.
- Follow established repository conventions and the closest applicable
  `AGENTS.md`.
- Add or update focused tests for non-trivial behavior when the project has a
  test structure.
- Run the relevant checks and report anything that could not be verified.
- Do not bypass or weaken checks to make work pass.

## Boundaries

- Never commit secrets, credentials, private data, or local `.env` contents.
- Ask before expanding scope, adding dependencies, changing public interfaces,
  performing migrations, or taking difficult-to-reverse actions.
- Do not overwrite unrelated work or use destructive commands without explicit
  authorization.
- Do not commit, push, open pull requests, merge, or change external systems
  unless explicitly requested.
- State important assumptions, risks, limitations, and verification results in
  the final handoff.

After adopting this template, replace or extend these instructions with the
project's actual structure, technology stack, commands, examples, and boundaries.
