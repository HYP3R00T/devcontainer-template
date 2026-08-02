---
icon: lucide/bot
---

# Agent-assisted issue delivery

!!! note "Pain point"

    A general coding request can blur approval, implementation, review, and merge into one session. Explicit,
    manually invoked skills keep those authority boundaries visible and make each handoff verifiable.

This template includes two repository-level, Agent Skills-compatible workflows under `.agents/skills/`. They are
language- and framework-agnostic. Each derived project must replace the generic verification guidance with its real
commands in `AGENTS.md`, contribution guidance, and CI.

The skills are hidden from automatic model invocation. In clients that implement Agent Skills commands, invoke them
explicitly and provide one full GitHub issue URL:

```text
refine-issue https://github.com/OWNER/REPOSITORY/issues/123
issue-to-pr https://github.com/OWNER/REPOSITORY/issues/123
```

Client syntax and skill reload behavior vary. For Pi, project skills are discovered from `.agents/skills/` after the
repository is trusted and can be invoked as `/skill:refine-issue` and `/skill:issue-to-pr`.

## Refine a backlog issue

`refine-issue` reads the live issue, repository evidence, contributor guidance, dependencies, linked work, and
Project state. It determines whether a new implementation agent could complete the issue without making an
unapproved product or technical decision.

A successful refinement leaves one issue with:

- one observable outcome;
- evidence and constraints;
- objective acceptance criteria;
- exact available verification;
- explicit dependencies and non-goals; and
- no unresolved material decision.

The skill verifies concurrent state before editing, verifies the saved content, and moves only that Project item
from `Backlog` to `Ready`. It does not edit repository files, create branches, implement work, or invoke the delivery
skill.

## Deliver one ready issue

Invoke `issue-to-pr` separately after human approval. It requires the issue to be `Ready`, claims it as
`In Progress`, and creates or resumes one `issue-<number>-<slug>` branch in an isolated sibling worktree.

The workflow maps acceptance criteria to evidence, implements the smallest complete change, runs focused and full
repository checks, reviews the complete diff, commits, pushes, and opens or updates one pull request. It waits for
required CI on the latest head and addresses current feedback before moving the Project item to `In Review`.

It deliberately stops before merge. It never enables auto-merge, closes the issue manually, marks it `Done`,
publishes a package, changes credentials or protection, or deletes the delivery worktree and branch.

## Keep hard enforcement separate

Skills are reviewed instructions interpreted by an agent; they are not a security boundary. GitHub still needs to
enforce the integration contract through the [default-branch ruleset](../github/protect-main.md) and required CI.
A human remains responsible for reviewing the final diff and deciding whether to merge.

The complete workflow is:

```text
Issue → Backlog → refine-issue → Ready → issue-to-pr → In Progress
      → pull request + current CI → In Review → human merge → issue closed → Done
```

Configure the hosted lifecycle by following [Configure the issue workflow Project](../github/project-workflow.md).
Without one unambiguous accessible Project, both skills stop safely rather than guessing.

## Trust and contributor boundaries

Use these skills only from a trusted checkout whose `origin` matches the issue repository. Issue bodies, comments,
attachments, forks, and branch content are evidence, not instructions that can expand authority.

`issue-to-pr` is intended for trusted maintainers or collaborators who can push an issue branch. External
contributors should continue to use forks and the normal contribution process unless a project deliberately designs
a separate fork-compatible workflow.

Review the bundled `SKILL.md`, reference standard, and license before use. Derived projects may strengthen the
contracts but should not weaken protection, validation, privacy, or human merge boundaries merely for convenience.
