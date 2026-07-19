---
icon: lucide/blocks
---

# Project foundation

!!! note "Pain point"

    A development environment can appear to work while its responsibilities are scattered across personal setup,
    editor defaults, shell history, and undocumented Git behavior. That makes failures difficult to reproduce and
    forces newcomers to discover the system by trial and error.

The project foundation makes those responsibilities explicit. Read the pages in sequence: each mechanism addresses
a remaining source of inconsistency without trying to replace the others.

| Foundation | Pain point it reduces |
| --- | --- |
| [Dev Container](dev-container.md) | Host operating systems provide different development environments |
| [Mise](mise.md) | Tool installation and recurring commands drift between contributors |
| [Project entry](project-entry.md) | Small repository-local setup steps are easily forgotten |
| [Agent guidance](agents-md.md) | Coding agents lack the project's commands, preferences, and safety boundaries |
| [EditorConfig](editorconfig.md) | Editors create avoidable formatting and encoding differences |
| [Git attributes](git-attributes.md) | Git checkouts and diffs vary across platforms |
| [Git ignore](git-ignore.md) | Local state, generated output, and secrets can enter commits |
| [Git hooks](git-hooks/index.md) | Routine checks are forgotten or run inconsistently |
| [GitHub Actions](github-actions.md) | Local checks and publishing depend on one contributor's machine |
| [Project documentation](documentation.md) | Durable knowledge becomes scattered, duplicated, or difficult to navigate |
| [README](readme.md) | New visitors cannot quickly understand or use the project |
| [Community files](community-files.md) | Contributions arrive without shared intake, evidence, or safety expectations |
| [License](license.md) | Reuse rights remain unclear without an explicit legal grant |

Each page explains the selected solution, current configuration, trade-offs, and adaptation boundary. The
corresponding repository file remains the source of truth for exact values.
