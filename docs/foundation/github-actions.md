---
icon: lucide/workflow
---

# Continuous integration with GitHub Actions

!!! note "Pain point"

    Local checks run quickly, but contributors can skip them and machines can produce different results. A project
    also needs a trusted place to repeat required checks and publishing work without depending on one developer's
    computer.

GitHub Actions runs version-controlled workflows on clean hosted runners. This template uses it for two distinct
jobs: verifying repository quality and publishing the documentation site.

## Configured workflows

| Workflow | File | Responsibility |
| --- | --- | --- |
| Quality Gate | `.github/workflows/ci.yaml` | Run the same `prek` suite used during local development |
| Documentation | `.github/workflows/docs.yml` | Validate documentation pull requests and deploy the Zensical site from the default branch |

Keeping them separate gives each workflow focused permissions, triggers, status, and failure reporting.

## Quality Gate

The Quality Gate runs for pull requests targeting `main`, pushes to `main`, and manual dispatches.

| Configuration | Why it is selected |
| --- | --- |
| `contents: read` | The checks need repository content but must not modify the repository |
| `persist-credentials: false` | Removes the checkout token after fetching so later checks cannot reuse it implicitly |
| Concurrency with cancellation | Stops obsolete runs when newer commits arrive on the same reference |
| `j178/prek-action@v2` | Runs `.pre-commit-config.yaml` instead of maintaining a second CI-only check list |
| `--skip no-commit-to-branch` | Leaves direct-commit prevention to the local hook and hosted branch rules |
| Job name `Repository checks` | Provides the stable status context required by the default-branch ruleset |

The workflow deliberately contains no placeholder build, test, type-check, or language-lint steps. A derived project
should add real project-specific verification only after its runtime and test strategy exist.

The Quality Gate skips `no-commit-to-branch` because CI checks the branch after checkout, not while a contributor is
creating a commit. A legitimate push produced by merging a pull request therefore has `main` checked out. Running
the local branch guard in that context would reject the protected integration path it is meant to support. The hook
still blocks ordinary local commits, while the GitHub ruleset prevents direct hosted updates to `main`.

## From feedback to enforcement

```text
prek Git hook → fast local feedback
GitHub Actions → clean-runner verification
GitHub ruleset → prevents merging when verification fails
```

A workflow failure is informational until a GitHub ruleset requires its status. The documented
[default-branch ruleset](../github/protect-main.md) requires `Repository checks`, turning the Quality Gate into an
integration constraint.

For public repositories, configure the separate [external-contribution approval gate](../github/secure-contributions.md).
It lets a maintainer inspect an external fork's changes before GitHub executes the requested pull-request workflow.

Changing the job name changes its status context. Update the ruleset at the same time or pull requests may wait for
a check that can no longer appear.

## Documentation validation and deployment

The Documentation workflow builds relevant changes in pull requests targeting `main` or `master`, catching broken
navigation and configuration before merge. After those changes reach the default branch, it builds again and deploys
the resulting site. Path filters prevent documentation work from running for unrelated code changes.

| Permission or step | Responsibility |
| --- | --- |
| `contents: read` | Read the Markdown and Zensical configuration |
| `pages: write` | Publish the generated Pages artifact |
| `id-token: write` | Authenticate the deployment through GitHub's OpenID Connect flow |
| `github-pages` environment | Record the deployment and expose its resulting URL |
| `astral-sh/setup-uv` | Install uv without managing a global Python environment manually |
| `uvx zensical build --clean` | Resolve Zensical in isolation and build a fresh site |
| Conditional Pages artifact and deploy actions | Upload and publish `site/` only for pushes to the default branch |

The workflow file can describe deployment, but the generated repository must still enable GitHub Pages with
GitHub Actions as its source. That hosted setting belongs to the [GitHub setup](../github/index.md) layer.

## Verify and adapt

Review workflow runs under the repository's **Actions** tab. A successful local command is useful evidence, but it
does not replace the hosted run required by the ruleset.

When adding a project-specific check, expose its implementation as a Mise task where practical and call that task
from GitHub Actions. Grant only the permissions the new step genuinely needs, keep job names unique, and document
any status name required by a ruleset.

## Official documentation

- [GitHub Actions documentation](https://docs.github.com/en/actions)
- [Workflow syntax](https://docs.github.com/en/actions/reference/workflows-and-actions/workflow-syntax)
- [Using jobs](https://docs.github.com/en/actions/how-tos/write-workflows/choose-what-workflows-do/use-jobs)
- [GitHub Pages custom workflows](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages)
