---
icon: lucide/wrench
---

# Tool management with Mise

!!! note "Pain point"

    Asking contributors to install tools manually produces different versions, missing commands, and setup notes
    that drift away from CI. Even when everyone installs the correct tools once, updates must be coordinated later.

Mise defines which development tools and shared commands the repository uses. The committed configuration is the
human-readable requirement; the lockfile records the exact accepted resolution.

## Responsibilities

| Area | Configuration |
| --- | --- |
| Shared tools | `[tools]` |
| Mise behavior | `[settings]` |
| Project-entry automation | `[hooks]` |
| Contributor commands | `[tasks]` |
| Local environment loading | `[env]` |

Tools use readable requirements such as `latest`. `mise.lock` records the exact versions and integrity information currently accepted by the project. This gives maintainers an explicit upgrade point without making the configuration difficult to understand.

## Platform behavior

Cross-platform tools install everywhere. Unix-only tools declare Linux and macOS restrictions, so Windows compatibility never weakens the reference environment.

The template enables Mise's GitHub credential integration so authenticated Git operations can be reused for tool
downloads. Local secrets remain outside `mise.toml` and may be loaded from the ignored `.env` file.

## Maintenance rule

After changing tools, run `mise install` and update `mise.lock`. After adding a recurring command, expose it as a Mise task and call that task from CI rather than duplicating its implementation.

Use `mise tasks` to discover repository commands and `mise ls --current` to inspect resolved tools. A derived project
should add only the runtimes and tasks it actually uses.

## Official documentation

- [Mise documentation](https://mise.jdx.dev/)
- [Mise tool management](https://mise.jdx.dev/dev-tools/)
- [Mise lockfiles](https://mise.jdx.dev/dev-tools/mise-lock.html)
