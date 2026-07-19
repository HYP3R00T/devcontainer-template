---
icon: lucide/shield-check
---

# Secure external contributions

!!! note "Pain point"

    A public repository allows people outside the project to propose changes from forks. Opening a pull request can
    also request GitHub Actions work, so an untrusted proposal may consume runner capacity or attempt to exploit a
    workflow before a maintainer has inspected it.

Open contribution and automatic execution are separate decisions. The repository can accept pull requests from
anyone while requiring a maintainer to approve workflow execution for external contributors.

## Require approval before workflows run

Configure the repository under **Settings → Actions → General → Approval for running fork pull request workflows
from contributors** and select **Require approval for all external contributors**.

With this policy, a pull request from an external fork can be opened and reviewed, but its requested workflow run
waits until someone with write access approves it. Choose the all-external-contributors option rather than a
first-time-only option: once a small contribution has been merged, GitHub no longer considers that person a
first-time contributor.

Workflow approval means only “allow this proposed code to execute in the configured runner context.” It does not
approve the pull request, satisfy a required review, or authorize merging. Those decisions happen separately.

## Review before approving execution

Inspect the complete pull-request diff, with particular attention to:

- files under `.github/workflows/` and any local Actions they call;
- scripts, task definitions, package manifests, and installation hooks executed by CI;
- changes that download or execute content from the network;
- attempts to read environment variables, credentials, runner files, caches, or artifacts; and
- changes that replace a hosted runner with a self-hosted runner.

Do not approve a run merely because the proposed application change looks harmless. A workflow can execute changed
repository scripts even when the workflow YAML itself was not modified.

## Keep the approved run contained

Approval is one layer, not a sandbox guarantee. Retain these boundaries:

| Boundary | Recommended policy | Why |
| --- | --- | --- |
| Workflow event | Use `pull_request` for untrusted validation | Fork runs receive a restricted context |
| Token | Set default workflow permissions to read-only and narrow them per job | Limits repository changes after compromise |
| Secrets | Do not expose secrets to fork pull-request jobs | Untrusted code can print or transmit any value it can read |
| Runner | Use GitHub-hosted runners for public pull requests | A fresh hosted runner does not expose a persistent project machine |
| Deployment | Trigger only from the protected default branch | Validation cannot publish or modify an environment |
| Actions | Allow only required Actions and pin trusted revisions when the project adopts that policy | Reduces third-party supply-chain exposure |

Avoid `pull_request_target` for workflows that execute, build, or inspect untrusted code. It runs in the privileged
base-repository context and is not held by the fork-workflow approval policy. Privileged follow-up workflows must
never check out or execute the pull request's code or trust its artifacts without a separate security design.

Do not use self-hosted runners for public pull-request validation. Once untrusted code executes there, it can target
the runner machine, persistent files, network access, and later jobs; approving the run does not make that code
safe.

## Keep contribution access separate

An external contributor does not need collaborator access. The normal path is:

```text
Issue or proposal → maintainer agreement → contributor fork → pull request
→ maintainer reviews diff → maintainer approves workflow → checks and review → merge decision
```

Ask contributors to discuss substantial work in an issue before implementation. A maintainer comment or an
“accepted” label is a clearer signal than requiring assignment, because assignment eligibility can depend on
repository permissions and prior participation. Small obvious corrections may still arrive directly.

Issue agreement reduces wasted effort; it is not a security boundary and does not guarantee merge. Grant write
access only when a recurring contributor becomes a trusted maintainer who needs repository-level responsibilities.

## Respond to abuse without closing contribution

Public repositories cannot use the approval gate as a permanent whitelist for opening pull requests. If submission
volume becomes abusive, GitHub provides temporary interaction limits and a cap on concurrent pull requests from
users without write access. Use those moderation controls when the problem occurs instead of requiring every
legitimate contributor to become a collaborator.

## Verify the policy

Use an account without repository access to open a harmless pull request from a fork. Confirm that:

1. the pull request can be opened;
2. its workflow run waits for maintainer approval;
3. the run uses a GitHub-hosted runner with read-only repository permissions;
4. no deployment job runs for the pull-request event; and
5. approving the workflow does not approve or merge the pull request.

Repeat this verification after changing Actions policies, workflow triggers, runner types, token permissions, or
organization-level settings.

## Official documentation

- [Managing GitHub Actions settings](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/enabling-features-for-your-repository/managing-github-actions-settings-for-a-repository)
- [Secure use reference for GitHub Actions](https://docs.github.com/en/actions/reference/security/secure-use)
- [Events that trigger workflows](https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows)
- [Limiting repository interactions](https://docs.github.com/en/communities/moderating-comments-and-conversations/limiting-interactions-in-your-repository)
