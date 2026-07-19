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

Create the labels expected by [Dependabot](dependabot.md) when enabling automated dependency updates.

## Official documentation

- [Creating a repository from a template](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template)
- [About GitHub rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/about-rulesets)
