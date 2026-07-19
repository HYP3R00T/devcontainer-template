---
icon: lucide/eye-off
---

# Git ignore

!!! note "Pain point"

    Development creates caches, generated output, local overrides, and secret-bearing environment files. Without a
    shared exclusion policy, those machine-local artifacts can enter commits and distract from project content.

`.gitignore` defines untracked paths that Git should normally leave out of commits. It protects the repository from machine-local state, generated output, caches, and secret-bearing local files.

## Current rules

| Pattern | Reason |
| --- | --- |
| `.env` and `.env.*` | Keep local environment values and secrets untracked |
| `!.env.example` | Allow a value-free environment-variable template |
| `mise.local.toml` and `mise.*.local.toml` | Keep contributor-specific Mise overrides local |
| `.cache/` | Ignore general local tool caches |
| `.rumdl_cache/` | Ignore the rumdl incremental cache |
| `site/` | Ignore the generated Zensical site |

## Important boundary

Ignore rules affect untracked files. Adding a tracked path to `.gitignore` does not remove it from Git history or the index. If a path was committed accidentally, investigate its contents first, especially for secrets, before changing tracking state.

Check which rule ignores a path with:

```bash
git check-ignore -v -- .env
```

## Extending it

This template keeps only language-agnostic rules. When a project selects Python, Node.js, Rust, or another ecosystem, add the appropriate official patterns without duplicating existing entries. The [GitHub gitignore templates](https://github.com/github/gitignore) are the preferred starting point.

See the official [gitignore documentation](https://git-scm.com/docs/gitignore) for pattern precedence, negation, directory matching, and scope.
