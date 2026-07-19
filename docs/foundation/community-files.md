---
icon: lucide/users
---

# Community and contribution files

!!! note "Pain point"

    Without a visible contribution contract, ideas arrive in incompatible formats, substantial work begins before
    it is accepted, pull requests omit verification evidence, and sensitive reports may be disclosed publicly.

GitHub recognizes several version-controlled community files. This template uses them together to guide how people
propose work, implement it, request review, report risk, and participate in the project.

## Files and responsibilities

| File | Responsibility | Why it exists |
| --- | --- | --- |
| `CONTRIBUTING.md` | Define the complete contribution agreement | Gives humans and AI-assisted contributors one self-contained working method |
| `.github/ISSUE_TEMPLATE/bug_report.yml` | Collect reproducible defect evidence | Separates actual behavior, expected behavior, environment, and reproduction |
| `.github/ISSUE_TEMPLATE/feature_request.yml` | Explore a pain point and desired outcome | Discourages implementation before the proposal is understood and accepted |
| `.github/ISSUE_TEMPLATE/config.yml` | Disable blank issues | Keeps issue intake inside the supported structured paths |
| `.github/PULL_REQUEST_TEMPLATE.md` | Request implementation and verification evidence | Makes scope, related work, risks, documentation, and contributor ownership reviewable |
| `.github/CODEOWNERS` | Request review from responsible people or teams | Routes changes to owners without making approval mandatory by itself |
| `.github/CODE_OF_CONDUCT.md` | Define expected community behavior and enforcement | Provides a shared standard for safe participation and incident handling |
| `SECURITY.md` | Define a private vulnerability-reporting path | Keeps sensitive reports out of public issues and sets realistic expectations |
| `.github/FUNDING.yml` | Connect the repository to supported funding platforms | Makes sponsorship discoverable when the maintainer chooses to enable it |

## Contributor responsibility

The central rule in `CONTRIBUTING.md` is that a contributor must understand everything they submit. AI assistance is
allowed, but the person opening the pull request owns its correctness, security, scope, verification, licensing,
and maintainability. Work that cannot be explained is not ready to merge even when automated checks pass.

## Structured intake and delivery

```text
Bug or proposal
→ structured issue
→ maintainer alignment
→ focused branch
→ pull request with evidence
→ automated checks and review
→ protected integration
```

Issue forms collect information before work becomes implementation. The pull-request template then asks what
changed, why it changed, how it was verified, and which risks remain. These files guide behavior; GitHub rulesets
and required checks provide the hard integration boundary.

## Important boundaries

CODEOWNERS automatically requests review, but owner approval becomes mandatory only when a branch rule requires it.
The solo-maintainer ruleset deliberately leaves that requirement disabled because authors cannot approve their own
pull requests.

`SECURITY.md` prefers GitHub private vulnerability reporting, but the repository owner must enable that hosted
feature separately. The fallback email, CODEOWNERS account, funding recipient, moderation contact, labels, and
other personal values must be reviewed when creating a project from the template.

## Adapt carefully

Keep these files aligned. If issue intake changes, update `CONTRIBUTING.md` and the forms together. If review
ownership changes, update CODEOWNERS and the corresponding ruleset. Remove funding configuration when the derived
project does not accept sponsorship rather than leaving another maintainer's account in place.

## Official documentation

- [Setting up a repository for healthy contributions](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions)
- [Issue forms](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/syntax-for-issue-forms)
- [Pull-request templates](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/creating-a-pull-request-template-for-your-repository)
- [CODEOWNERS](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners)
- [Security policies](https://docs.github.com/en/code-security/getting-started/adding-a-security-policy-to-your-repository)
