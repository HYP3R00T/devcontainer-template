---
icon: lucide/bot
---

# Dependabot

!!! note "Pain point"

    GitHub Actions and other dependencies continue changing after a project is created. Checking every upstream
    release manually is easy to postpone, while ungrouped automated updates can overwhelm a small project with
    maintenance pull requests.

Official references: [Dependabot options](https://docs.github.com/en/code-security/reference/supply-chain-security/dependabot-options-reference), [managing labels](https://docs.github.com/en/issues/using-labels-and-milestones-to-track-work/managing-labels), and [`gh label create`](https://cli.github.com/manual/gh_label_create).

## Purpose

Dependabot checks the GitHub Actions used by this repository and opens pull requests when updates are available. The configuration lives in [`.github/dependabot.yml`](../../.github/dependabot.yml).

The weekly schedule keeps automation current without generating daily pull-request noise. Security updates are handled independently by GitHub's Dependabot security-update features, so routine version checks do not need to run every day.

All Action updates are grouped into one pull request. This reduces maintenance work, but an incompatible update can temporarily hold back the rest of the group. Split the group only if that becomes a recurring problem.

## Create the labels

Dependabot expects the `dependencies` and `ci` labels configured in `.github/dependabot.yml` to exist in the repository.

With the [GitHub CLI](https://cli.github.com/), authenticate and run these commands from the repository:

```bash
gh auth login
gh label create dependencies --description "Dependency updates" --color 0366D6 --force
gh label create ci --description "Continuous integration and automation" --color 5319E7 --force
```

The `--force` option makes the commands reusable: an existing label is updated instead of causing the command to fail. To configure another repository without changing directories, add `--repo OWNER/REPOSITORY` to each `gh label create` command.

Labels can also be created in the GitHub web interface under **Issues → Labels → New label**.

## Adapt the template

Replace the account in `assignees` with a maintainer who can be assigned in the new repository. Add another Dependabot ecosystem only after its actual dependency manifest exists; unused ecosystem entries do not belong in the template.
