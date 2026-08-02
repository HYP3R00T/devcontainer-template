---
icon: lucide/settings
---

# GitHub setup

!!! note "Pain point"

    A GitHub template copies repository files, but hosted settings such as rulesets, Pages, Projects, and private
    vulnerability reporting are not activated by those files. The repository can therefore describe a
    protected workflow without GitHub actually enforcing it.

Some parts of a project live in the repository; others exist only as settings on GitHub. A repository created
from a template receives the template files, but its hosted settings must be configured separately.

This distinction answers a common source of confusion: committing a JSON example, workflow, or CODEOWNERS file may
describe part of a policy, but GitHub does not automatically import every repository setting from the template.
An administrator must apply the hosted portion in each generated repository.

## Three kinds of project control

| Kind | Where it lives | How it works |
| --- | --- | --- |
| Versioned configuration | Repository files | Tools and automation read it directly |
| Guidelines | Documentation, issues, and review guidance | A person or agent interprets it |
| Hosted configuration | GitHub repository settings | GitHub enforces it after an administrator enables it |

EditorConfig, Git attributes, Git hooks, and workflows are versioned configuration. Contribution guidance and
review expectations describe decisions that still require judgment. Rulesets, Pages, private
vulnerability reporting, Projects, and repository permissions are hosted configuration.

This section documents hosted configuration separately because committing a workflow does not make its result a
required check, and describing a protected branch does not protect it. Each setup page provides the GitHub web
path and a command-line method when GitHub exposes one.

## Begin with the integration boundary

Configure [default-branch protection](protect-main.md) first. It turns the repository's existing Quality Gate
from feedback into an integration requirement and prevents accidental changes from bypassing pull-request
review.

Then configure [secure external contributions](secure-contributions.md) so workflow runs requested by external
forks wait for maintainer inspection and approval. Branch protection controls what may enter the default branch;
workflow approval controls when untrusted proposals may consume computation.

Create the labels expected by [Dependabot](dependabot.md) when enabling automated dependency updates. When the
issue queue needs explicit readiness and delivery state, configure the separate
[issue workflow Project](project-workflow.md) used by the repository's manual agent skills.

## Configure only what the project will use

Hosted features solve different coordination problems and should not all be enabled by habit:

| Setting | When it becomes useful |
| --- | --- |
| Default-branch ruleset | Immediately; it protects the shared integration boundary |
| External workflow approval | Immediately for public repositories that run pull-request workflows |
| GitHub Pages | When this Zensical handbook should be published |
| Private vulnerability reporting | When the public repository needs a safe channel for sensitive reports |
| Merge methods | When maintainers decide which histories contributors may create |
| GitHub Projects | When issue priority, dependencies, and status need a shared view |
| Discussions | When the project has a community need that does not fit actionable issues |
| Milestones | When accepted issues belong to a real release or delivery outcome |

For a solo maintainer, begin with the ruleset, Pages when desired, and private vulnerability reporting for a public
project. Add a Project when the issue queue becomes difficult to prioritize in isolation. Discussions and
milestones are not signs of maturity by themselves; unused coordination surfaces create more places to monitor.

After applying a hosted setting, verify its behavior rather than relying on the saved configuration. Open a test
pull request, confirm the expected checks appear, inspect the available merge methods, exercise Project item
transitions when configured, and confirm that Pages or private reporting is reachable through the repository
interface.

## Official documentation

- [Creating a repository from a template](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template)
- [About GitHub rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets)
