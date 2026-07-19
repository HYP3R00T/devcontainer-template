---
icon: lucide/bot
---

# Agent guidance

!!! note "Pain point"

    Coding agents can inspect a repository, but they do not automatically know which commands are authoritative,
    which engineering trade-offs the project prefers, or which actions require permission. Repeating that context
    in every conversation is slow and inconsistent.

`AGENTS.md` is a predictable, provider-neutral place for instructions that help coding agents work effectively in
a repository. It complements the README and contribution guide: those files primarily support people, while
`AGENTS.md` gives agents concise operational context.

The file is guidance, not enforcement. Tests, hooks, continuous integration, permissions, and repository rules
must enforce requirements that can be evaluated mechanically.

## What the template provides

The starter file deliberately contains only information that is true before a project chooses its language or
framework:

- **Commands** list the current setup and verification entry points.
- **Approach** encourages understanding, reuse, native capabilities, and the smallest complete solution.
- **Verification** requires agents to preserve existing work and validate non-trivial changes.
- **Boundaries** protect secrets, unrelated changes, external systems, and actions that require authorization.

It does not prescribe a particular AI provider, development lifecycle, MCP server, skill, subagent structure, or
architectural-decision process. Those choices depend on the project and should not be implied by a general-purpose
template.

## Adapt it when creating a project

Treat the included file as a safe starting point, not finished project configuration. After selecting a technology
stack, update it with information an experienced contributor would need to work without guessing:

1. Replace the generic project description with the actual purpose and important non-goals.
2. Add exact install, build, test, lint, format, type-check, and local-run commands.
3. Identify important directories and generated or vendor-managed paths that should not be edited.
4. Record established language, framework, naming, testing, and error-handling conventions.
5. Add concise examples when an example communicates the expected pattern better than prose.
6. State which actions are always allowed, which require approval, and which are prohibited.
7. Remove template instructions that no longer describe the adapted repository.

Commands should appear early and include the flags contributors actually use. An inaccurate command is worse than
an omitted one because an agent may repeatedly execute it and optimize around the resulting failure.

## Keep instructions effective

Prefer concrete direction:

```markdown
Run focused unit tests with `pytest tests/unit -q`.
Ask before changing database migrations.
Never edit generated files under `dist/`.
```

Avoid vague or aspirational direction:

```markdown
Write excellent code.
Follow all best practices.
Use the best tools available.
```

Keep one authoritative copy of each rule. Link to detailed repository documentation when an agent needs awareness
of it; do not reproduce entire contribution guides or architecture manuals inside `AGENTS.md`.

For a large repository, add a nested `AGENTS.md` only when a subtree genuinely has different commands,
conventions, or boundaries. The closest applicable file can then provide local guidance without making the root
file enormous.

## Maintain it from observed friction

Review `AGENTS.md` when commands, project structure, or safety boundaries change. Add guidance after a repeated
agent mistake reveals missing context; do not predict every possible mistake in advance. Remove obsolete or
duplicated instructions before the file becomes an operating manual no one can reliably absorb.

The objective is not to control every step an agent takes. It is to make the preferred path obvious, the relevant
checks discoverable, and dangerous assumptions visible before they become changes.

## Further reading

- [AGENTS.md open format](https://agents.md/)
- [GitHub: How to write a great `agents.md`](https://github.blog/ai-and-ml/github-copilot/how-to-write-a-great-agents-md-lessons-from-over-2500-repositories/)
- [Ponytail](https://github.com/DietrichGebert/ponytail), an example of concise simplicity-oriented agent guidance
