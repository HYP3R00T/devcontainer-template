---
icon: lucide/sliders-horizontal
---

# Adapt the template

The template supplies project-agnostic foundations. A new project must replace identity and add only the technical and operational decisions its product requires.

## Replace project identity

Review the repository name, owner, descriptions, links, badges, maintainer information, contact details, funding configuration, Code Owners, Dependabot assignees, license holder, documentation configuration, and security contact method.

## Add the project-specific layer

Once the language and architecture are known, add:

- runtimes and developer tools through Mise;
- official ecosystem ignore and attribute rules;
- formatters, linters, type checks, and tests;
- repeatable commands as Mise tasks;
- CI checks calling those same commands;
- architecture and domain documentation that explain stable boundaries; and
- release, deployment, monitoring, and security mechanisms required by the product.

Do not keep template guidance that is false for the resulting project. Do not add empty configuration for anticipated tools. The adapted repository should describe the system that exists, while issues and pull requests preserve how it reached that state.
