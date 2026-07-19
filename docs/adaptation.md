---
icon: lucide/sliders-horizontal
---

# Adapt the template

!!! note "Pain point"

    A generated repository initially contains the template's identity and only language-agnostic behavior. Leaving
    those values unchanged misrepresents ownership; adding speculative project configuration creates maintenance
    work before the product has made the corresponding decisions.

The template supplies project-agnostic foundations. A new project must replace identity and add only the technical
and operational decisions its product requires. Adaptation is not a one-time search-and-replace operation: first
remove the template owner's identity, then introduce project decisions as they become true.

## Replace project identity

Review the repository name, owner, descriptions, links, badges, maintainer information, contact details, funding
configuration, Code Owners, Dependabot assignees, license holder, documentation configuration, and security contact
method.

The most visible locations include `README.md`, `zensical.toml`, `LICENSE`, `SECURITY.md`, `.github/CODEOWNERS`,
`.github/FUNDING.yml`, and `.github/dependabot.yml`. Search the complete repository for the template owner and
repository name; identity can also appear in links and examples.

Remove an optional mechanism when the new project does not support it. For example, do not leave another person's
funding account or an unattended security address merely because the file was copied successfully.

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

## Adapt in a safe order

1. Replace project identity, ownership, licensing, and contact information.
2. Write the product purpose, supported users, and important non-goals in the README and documentation.
3. Add only the runtime and dependencies required by the first accepted increment.
4. Expose repeatable development commands through Mise.
5. Add focused checks for the chosen stack and call the same commands from CI.
6. Configure the hosted GitHub settings described in [GitHub setup](github/index.md).
7. Rebuild the container from a clean checkout and follow the onboarding instructions as a newcomer would.

## Know when adaptation is complete

The repository is ready to begin product work when a new contributor can identify the project, enter the reference
environment, discover its commands, run its checks, and understand how a change reaches the default branch without
depending on private instructions.

Run the baseline verification after adaptation:

```bash
mise install
prek run --all-files
uvx zensical build --clean
```

Then run the project-specific build and tests added by the derived project. A passing template check confirms the
foundation; it cannot prove that the application itself is correct.
