---
icon: lucide/book-open
---

# Project documentation

!!! note "Pain point"

    Repository behavior becomes difficult to maintain when important reasoning exists only in conversations or in
    one contributor's memory. Documenting everything creates a different burden: duplicated, outdated prose that
    readers cannot navigate.

This template keeps durable project knowledge as Markdown and uses Zensical as a presentation layer. The Markdown
remains readable in GitHub and editors even when the documentation site is not running.

## Documentation stack

| Layer | Configuration | Responsibility |
| --- | --- | --- |
| Content | `docs/**/*.md` | Explain pain points, decisions, configuration, trade-offs, and maintenance |
| Structure and rendering | `zensical.toml` | Define site identity, navigation, theme, and Markdown extensions |
| Markdown policy | `rumdl.toml` | Define repository-wide Markdown rules |
| Local preview | `mise run docs` | Run `uvx zensical serve` without adding an application dependency |
| Publishing | `.github/workflows/docs.yml` | Build a clean site and deploy it through GitHub Pages |

The generated `site/` directory is ignored because it is build output. The Markdown and configuration—not the
rendered HTML—are the version-controlled source.

## Content model

Each substantive page begins with one visually distinct **Pain point**. The remaining article explains the selected
approach in ordinary prose:

```text
Pain point
→ chosen approach
→ current configuration
→ reasons for those choices
→ trade-offs and limitations
→ verification and adaptation
```

Use the structure as a reasoning guide, not a mandatory list of headings. A short page should stay short when its
topic does not need every section.

## Zensical configuration

Navigation is explicit so the visible learning path remains deliberate and matches the `docs/` folder structure.
The theme enables navigation, search, code-copying, annotations, and light/dark palettes. Admonitions provide the
Pain point callout, while selected PyMdown extensions support details, tabbed content, and fenced diagrams when a
diagram materially improves understanding.

Project identity in `zensical.toml` belongs to this template. A generated repository must replace the site name,
description, repository link, author, and copyright details.

## Markdown policy

Rumdl enforces core Markdown structure while `rumdl.toml` disables rules that would over-constrain this handbook:

| Disabled rule | Reason |
| --- | --- |
| `MD013` | Long links and informative tables should not be rewritten merely to satisfy a fixed line length |
| `MD033` | The repository README uses limited inline HTML for its centered landing-page layout |
| `MD034` | Bare URLs are permitted where forcing link labels would reduce clarity |
| `MD036`, `MD037`, `MD049` | Emphasis choices are not treated as structural correctness |
| `MD044` | A generic spelling list cannot reliably validate every product and tool name |
| `MD046` | Fenced and indented code styles are both accepted where Markdown context requires them |
| `MD059` | Link text is reviewed for clarity instead of enforced through a generic wording rule |

Disabling a rule is not permission for inconsistent writing. It means the rule's automated judgment is not reliable
enough to become repository policy.

## Preview and verify

Run the local preview while writing:

```bash
mise run docs
```

Before integration, validate both source and rendering:

```bash
rumdl check docs
uvx zensical build --clean
```

The documentation workflow performs the same clean build for relevant pull requests, then builds and publishes
again after those changes reach the default branch. Broken navigation or theme configuration can still differ from
Markdown lint, so a complete site build is the authoritative rendering check.

## Official documentation

- [Zensical documentation](https://zensical.org/docs/)
- [Rumdl documentation](https://rumdl.dev/)
- [GitHub Pages documentation](https://docs.github.com/en/pages)
