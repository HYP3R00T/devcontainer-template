---
icon: lucide/container
---

# DevContainer Template

A reusable starting point for building understandable, auditable, and maintainable projects.

!!! note "Pain point"

    Starting a project repeatedly consumes time on environment setup, tool installation, repository hygiene, and
    contribution rules before useful product work can begin. When every project solves these concerns differently,
    people and automation must relearn the development environment each time.

This template provides a small language-agnostic baseline and explains why each part exists. The repository files
remain the source of truth for exact behavior; this handbook builds the mental model needed to use and adapt them.

## Reading path

1. Read [Why this template exists](introduction/why-template.md) and [The project model](introduction/project-model.md).
2. Follow [Getting started](introduction/getting-started.md) to enter the reference environment.
3. Study the [project foundation](foundation/index.md) in the order its pieces are introduced.
4. Learn the [development workflow](workflow/index.md) used to keep changes small and traceable.
5. Complete the required [GitHub setup](github/index.md) that repository files cannot apply automatically.
6. [Adapt the template](adaptation.md) when the project makes its language and product decisions.

## How the pieces stay in sync

| Layer | Responsibility |
| --- | --- |
| Repository files | Define the environment, tools, checks, templates, and workflows that exist now |
| GitHub settings | Enforce hosted behavior such as protected branches and required checks |
| Documentation | Explain the pain points, decisions, trade-offs, and maintenance boundaries |
| Issues and pull requests | Preserve why work was accepted, how it changed, and how it was verified |

The goal is not maximum automation. It is a baseline that a human can understand, an agent can follow, and CI can
verify without any one of them becoming the sole source of project knowledge.
