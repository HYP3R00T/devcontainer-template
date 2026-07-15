---
icon: lucide/blocks
---

# Foundations

Foundations establish the conditions under which development happens. They exist before application architecture and should remain understandable without knowing the eventual programming language.

| Foundation | Question it answers |
| --- | --- |
| [Dev container](../concepts/dev-container.md) | Where does development happen? |
| [Mise](../concepts/mise.md) | Which tools and shared commands does the project use? |
| [Project entry](../concepts/project-entry.md) | Which small setup actions must be true when work begins? |
| [EditorConfig](../concepts/editorconfig.md) | How should compatible editors create text? |
| [Git attributes](../concepts/git-attributes.md) | How should Git classify and normalize tracked files? |
| [Git ignore](../concepts/git-ignore.md) | Which local artifacts must stay outside version control? |
| [Git hooks](../concepts/git-hooks/index.md) | Which checks should run around Git operations? |
| [README](readme.md) | How should the project introduce itself to users? |

Each page explains purpose, responsibility, trade-offs, and maintenance. The corresponding repository file remains the source of truth for exact configuration.

Foundations should be changed deliberately. Add a mechanism because several projects genuinely need it, not because it might become useful someday.
