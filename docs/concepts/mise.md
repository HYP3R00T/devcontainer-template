---
icon: lucide/wrench
---

# Tool management with Mise

Mise answers a second question: **which tools and commands does this repository use?**

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

## Maintenance rule

After changing tools, run `mise install` and update `mise.lock`. After adding a recurring command, expose it as a Mise task and call that task from CI rather than duplicating its implementation.

## Official documentation

- [Mise documentation](https://mise.jdx.dev/)
- [Mise tool management](https://mise.jdx.dev/dev-tools/)
- [Mise lockfiles](https://mise.jdx.dev/dev-tools/mise-lock.html)
