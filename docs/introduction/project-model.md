---
icon: lucide/boxes
---

# The project model

!!! note "Pain point"

    A generic template cannot know a future product's language, architecture, risks, or release model. Guessing
    those details creates unused configuration, while omitting every shared practice forces each project to rebuild
    its foundation.

The template separates reusable foundations from decisions that belong to the resulting project. It also separates
rules a machine can evaluate from expectations that require judgment.

| | Project-agnostic | Project-specific |
| --- | --- | --- |
| **Hard constraints** | Valid configuration, clean tracked files, shared checks, and protected integration | Language tests, type checks, security scans, and deployment gates |
| **Soft constraints** | Focused changes, understandable work, traceability, and contributor ownership | Architecture, domain language, compatibility promises, and product priorities |

## Project-agnostic foundation

The template provides a reference environment, tool management, repository consistency, Git hooks, contribution
guidance, documentation, and CI integration. These mechanisms remain useful whether the application later uses
Python, JavaScript, Rust, infrastructure code, or several technologies together.

## Project-specific layer

A real project deliberately adds its runtime, dependency model, application structure, testing strategy, ownership
boundaries, security controls, release policy, and operational requirements. Add them when the product makes those
decisions—not because a generic checklist suggests that every repository must contain them.

## Put each decision in the correct layer

A written rule is not automatically enforced. Deterministic requirements that must block integration belong in
automation and GitHub rules. Contextual decisions belong in clear guidance and review. The objective is not to
automate every preference; it is to place each decision where it can remain truthful and maintainable.

When deciding where a new concern belongs, ask two questions:

1. Is this true for the generic template or only for the product being built?
2. Can a machine evaluate it reliably, or does it require contextual judgment?

| New concern | Appropriate layer |
| --- | --- |
| All tracked YAML must parse | Project-agnostic hard constraint |
| The application must pass its selected framework tests | Project-specific hard constraint |
| Pull requests should remain focused and explain risk | Project-agnostic soft constraint |
| Domain services may not access persistence directly | Project-specific soft constraint until an appropriate check exists |

Do not promote a preference into automation merely because a tool can approximate it. A noisy or brittle check
teaches contributors to bypass the system. Likewise, do not leave a stable, objective safety requirement only in
prose when CI can enforce it consistently.
