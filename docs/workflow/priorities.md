---
icon: lucide/list-ordered
---

# Priorities and dependencies

!!! note "Pain point"

    A backlog becomes misleading when priority means enthusiasm or age and every relationship is treated as a
    blocking dependency. Important risk can remain hidden behind easier or more visible work.

Priority expresses the order in which work creates the most value or removes the most risk. It should not be
confused with age, enthusiasm, implementation convenience, or workflow status.

Three questions are often mixed together:

| Question | Meaning |
| --- | --- |
| How important is it? | Priority |
| Can it begin yet? | Dependency or readiness |
| Is someone working on it? | Status |

A high-priority issue can remain blocked, while a lower-priority issue may be the best available work. Keeping the
questions separate makes the queue honest.

Consider, in order:

1. Security incidents, data loss, and actively harmful behavior.
2. Broken main-branch, release, or development workflows.
3. Work blocking several other accepted issues.
4. High user value, contractual commitments, or time-sensitive opportunities.
5. Maintenance that measurably reduces recurring cost or risk.
6. Everything else.

Use the list as a decision aid rather than a permanent numeric formula. When two issues appear equal, prefer the
one that tests a risky assumption, unblocks more accepted work, or produces useful feedback sooner. Revisit the
ordering when new evidence changes risk or value; a backlog is a current decision, not a promise made forever.

## Record only real dependencies

A dependency exists when the outcome of one issue cannot be completed or verified until another outcome exists.
“Touches the same component,” “would be convenient to do first,” and “is related to” are not blocking
dependencies.

Excessive dependency graphs make parallel work harder and often indicate that issues are organized around internal
components rather than demonstrable outcomes. If two issues must always move together, reconsider whether they are
actually one reviewable increment.

## Keep coordination lightweight

Use a GitHub Project when priority, status, and blocked work need to be visible together. Introduce a milestone only
when accepted issues genuinely belong to a planned release or delivery outcome; it is not a second status board.

For a small project, a board with **Backlog**, **Ready**, **In progress**, and **Done** is usually enough. Add fields
or views only when they answer a recurring coordination question. The project board organizes issues; it should not
become a second place where their scope and acceptance criteria must be maintained.
