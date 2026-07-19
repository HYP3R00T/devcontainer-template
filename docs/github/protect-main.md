---
icon: lucide/shield-check
---

# Protect the default branch

!!! note "Pain point"

    A CI workflow can report failure without preventing a merge, and a documented branch policy does not stop
    direct pushes, force-pushes, or deletion. The integration boundary remains dependent on memory until GitHub is
    configured to enforce it.

The default branch is the integration point for accepted work. Protect it after creating a repository from this
template so changes must arrive through pull requests and pass the repository checks before merging.

## Baseline policy

The recommended solo-maintainer policy:

- prevents deletion and force-pushes;
- requires changes to use a pull request;
- requires review conversations to be resolved;
- requires the `Repository checks` status from the Quality Gate workflow; and
- allows merge commits or squash merges.

It does not require an approving review or CODEOWNER review. GitHub does not allow an author to approve their own
pull request, so either requirement could lock a solo maintainer out when no bypass actor is configured.

## Ruleset JSON

Copy the following content into a temporary local file named `protect-main.json`. The file is an import payload,
not a repository configuration file; GitHub will not discover or apply it merely because it is committed.

```json
{
  "name": "protect-main",
  "target": "branch",
  "enforcement": "active",
  "bypass_actors": [],
  "conditions": {
    "ref_name": {
      "exclude": [],
      "include": [
        "~DEFAULT_BRANCH"
      ]
    }
  },
  "rules": [
    {
      "type": "deletion"
    },
    {
      "type": "non_fast_forward"
    },
    {
      "type": "pull_request",
      "parameters": {
        "required_approving_review_count": 0,
        "dismiss_stale_reviews_on_push": true,
        "required_reviewers": [],
        "require_code_owner_review": false,
        "require_last_push_approval": false,
        "required_review_thread_resolution": true,
        "allowed_merge_methods": [
          "merge",
          "squash"
        ]
      }
    },
    {
      "type": "required_status_checks",
      "parameters": {
        "do_not_enforce_on_create": false,
        "required_status_checks": [
          {
            "context": "Repository checks"
          }
        ],
        "strict_required_status_checks_policy": true
      }
    }
  ]
}
```

The portable example omits `id`, `source`, and `source_type`. GitHub adds those values after creating the ruleset;
an exported ruleset may contain values tied to its original repository.

## Understand the configuration

### Ruleset identity and scope

| Field | Selected value | Why this baseline uses it |
| --- | --- | --- |
| `name` | `protect-main` | Gives administrators a short, recognizable policy name. The name describes intent rather than a branch that may later be renamed. |
| `target` | `branch` | Applies the rules to branches. Tags and repository-wide push restrictions solve different problems and should use separate rulesets. |
| `enforcement` | `active` | Enforces the rules immediately. Use `evaluate` temporarily when introducing a policy to an active team that first needs to measure its impact. |
| `bypass_actors` | `[]` | Gives nobody a routine path around the policy. An administrator can still change the ruleset, but exceptional access is not built into everyday merging. |
| `include` | `~DEFAULT_BRANCH` | Protects whichever branch GitHub currently considers the default. The same JSON therefore works with `main` or another default-branch name. |
| `exclude` | `[]` | Makes no exception inside the selected default-branch target. Add exclusions only when a concrete branch policy requires them. |

Keeping the default branch symbolic is important for a reusable template. Hard-coding `refs/heads/main` would be
valid for this repository, but the imported policy would silently miss a renamed default branch.

### Branch integrity rules

| Rule | What GitHub blocks | Why it is recommended |
| --- | --- | --- |
| `deletion` | Deleting the protected branch | Prevents accidental removal of the repository's integration history and default collaboration target. |
| `non_fast_forward` | Force-pushing rewritten history | Keeps merged commit references stable for audits, links, releases, and other contributors. |
| `pull_request` | Updating the branch without a pull request | Creates a visible review and verification boundary even when one person performs the work. |

These rules protect integration history; they do not judge whether the implementation is good. The pull request,
automated checks, and maintainer review provide that evidence.

### Pull-request parameters

| Parameter | Selected value | Reason and trade-off |
| --- | --- | --- |
| `required_approving_review_count` | `0` | A solo maintainer cannot approve their own pull request. The PR remains mandatory, but a second person's approval is not assumed. |
| `dismiss_stale_reviews_on_push` | `true` | If approvals are required later, new reviewable commits invalidate old approval so it cannot apply to unseen code. With zero required approvals, this has no immediate effect. |
| `required_reviewers` | `[]` | Avoids assigning organization teams or path-specific reviewers that a reusable personal template cannot know. |
| `require_code_owner_review` | `false` | Prevents the sole CODEOWNER from being required to approve their own work. Enable it only when another eligible owner exists. |
| `require_last_push_approval` | `false` | Requiring another person to approve the latest push would block a solo maintainer. Teams can enable it to stop authors from approving code and then changing it. |
| `required_review_thread_resolution` | `true` | Prevents merging while review questions or requested changes remain visibly unresolved. |
| `allowed_merge_methods` | `merge`, `squash` | Supports preserving a meaningful branch history or combining a focused PR into one commit. Rebase merging is omitted to keep the baseline choices small. |

Requiring a pull request with zero approvals is still useful. It produces the comparison, CI result, review history,
and merge record that make a solo developer's change auditable without pretending another reviewer exists.

### Required status check

| Parameter | Selected value | Why it is recommended |
| --- | --- | --- |
| `context` | `Repository checks` | Matches the job name in `.github/workflows/ci.yaml`, which runs the repository's shared `prek` checks. |
| `strict_required_status_checks_policy` | `true` | Requires the PR to be tested with the latest default-branch code before merging, reducing integration surprises. |
| `do_not_enforce_on_create` | `false` | Applies the check whenever the protected reference is updated. The default branch already exists when this post-template policy is installed. |

The status-check rule is what turns CI from information into enforcement. Without it, the workflow can fail while
GitHub still permits the pull request to merge.

## Import through GitHub

1. Open the repository on GitHub.
2. Go to **Settings → Rules → Rulesets**.
3. Select **New ruleset → Import a ruleset**.
4. Choose the temporary `protect-main.json` file.
5. Review the target, rules, required check, and merge methods.
6. Create the ruleset.

GitHub supports importing exported ruleset JSON through this interface. Always review an imported policy before
activating it; repository plans and ownership models can affect the available rules.

## Create it with GitHub CLI

The GitHub CLI has no dedicated `gh ruleset` command, but `gh api` can call GitHub's repository-rulesets API.
Authenticate with an account that has repository Administration write permission, open a terminal in the target
repository, and run:

```bash
gh auth login
gh api --method POST repos/{owner}/{repo}/rulesets --input protect-main.json
```

`gh api` fills `{owner}` and `{repo}` from the current repository. Keep the JSON file outside the repository or
delete it after use unless the project deliberately chooses to version reusable administration payloads.

## Verify the result

Open **Settings → Rules → Rulesets** and confirm that `protect-main` is active and targets the default branch. Then
open a small test pull request and confirm that:

- GitHub prevents direct integration until `Repository checks` succeeds;
- unresolved review conversations block merging; and
- deletion and force-push options are unavailable for the protected branch.

If GitHub reports that `Repository checks` is missing, run the Quality Gate workflow once in the new repository
and verify that the job name in `.github/workflows/ci.yaml` has not been changed.

## Adapt for a team

When another person can review changes, consider setting `required_approving_review_count` to `1`. Enable
`require_code_owner_review` only when CODEOWNERS approval is genuinely required and an eligible reviewer other
than the pull-request author is available. Add bypass actors sparingly and document why they exist.

## Official documentation

- [Managing repository rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/managing-rulesets-for-a-repository)
- [Repository rulesets REST API](https://docs.github.com/en/rest/repos/rules)
- [`gh api` reference](https://cli.github.com/manual/gh_api)
