---
icon: lucide/panel-top
---

# README

Official references: [About repository READMEs](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes), [workflow status badges](https://docs.github.com/en/actions/how-tos/monitor-workflows/add-a-status-badge), and [Shields.io badges](https://shields.io/badges).

## Purpose

A README is the project's landing page. It should quickly explain what the project is, why it is useful, and how someone starts using it. It should not duplicate the full documentation, contribution guide, security policy, or development handbook.

Write for a prospective user first. Contributor setup belongs in `CONTRIBUTING.md`; detailed concepts, operations, and maintenance instructions belong in the documentation.

## Recommended structure

Use the smallest set of sections that accurately represents the project:

1. A centered project name and one-sentence value proposition.
2. Two or three important links, such as documentation, the primary package or product, and contribution guidance.
3. A small set of meaningful status badges.
4. One useful screenshot, demonstration, or compact workflow visual when the project has something worth showing.
5. A short description with enough context to understand the project.
6. A focused feature list.
7. Instructions for using the product or template.
8. Links to contribution and support policies.
9. License information and an optional maintainer signature.

Do not add a section merely because other READMEs contain it.

## Badges

Badges should communicate current, verifiable information. Good candidates include the required quality gate, package or release versions, supported platforms, and the license. Add a documentation badge only when its status communicates something readers genuinely need; a documentation link is usually clearer.

Avoid decorative technology badges, social counters, or badges for workflows and releases that do not exist. A workflow badge displays the latest status; it does not execute the workflow.

Keep badges near the project title and link each badge to the page that explains its result. Use one visual style consistently. This template uses Shields.io's rectangular `for-the-badge` style.

## Visuals

Use a screenshot or demonstration when it helps someone understand the product faster than prose. Keep it current and legible. Do not invent a diagram merely to fill the visual position; add a diagram only when the relationship it shows is itself important.

Until a real visual exists, use a non-rendering HTML comment as a placeholder. Do not commit placeholder images. Remove stale visuals when they no longer represent the project.

## Description and features

The description should answer three questions:

- What does the project provide?
- Who is it for?
- What important boundary or design choice should the reader understand?

Features should describe useful capabilities, not restate implementation details or advertise planned work. Every claim must be true in the current repository.

## Usage, not contributor setup

The primary instructions should explain how someone uses the project. For a library, show installation and a minimal working example. For an application, show how to access or operate it. For a template, show how to create a project from it.

Commands for developing, testing, or contributing to the repository belong in `CONTRIBUTING.md` or the developer documentation.

## Adapt the template

When creating a project from this template, review and replace:

- the project name, description, links, and visual;
- repository owner and repository name in links and badges;
- documentation, package, deployment, and release links;
- features and usage instructions;
- badges that do not apply to the new project;
- the license statement when the project uses a different license; and
- the maintainer name and profile link in the footer.

Remove any section that cannot be kept accurate. A shorter truthful README is better than a complete-looking README containing fiction.

## Maintenance

Review the README whenever the user-facing workflow, supported platform, documentation location, release channel, or project identity changes. Link to deeper information instead of allowing the README to grow into a second documentation site.
