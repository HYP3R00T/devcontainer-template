---
icon: lucide/list-ordered
---

# Priorities and dependencies

!!! note "Pain point"

    A backlog becomes misleading when priority means enthusiasm or age and every relationship is treated as a
    blocking dependency. Important risk can remain hidden behind easier or more visible work.

Priority expresses the order in which work creates the most value or removes the most risk. It should not be confused with age, enthusiasm, or implementation convenience.

Consider, in order:

1. Security incidents, data loss, and actively harmful behavior.
2. Broken main-branch, release, or development workflows.
3. Work blocking several other accepted issues.
4. High user value, contractual commitments, or time-sensitive opportunities.
5. Maintenance that measurably reduces recurring cost or risk.
6. Everything else.

Dependencies should describe real sequencing constraints. “Related to” is not the same as “blocked by.” Excessive dependency graphs make parallel work harder and often indicate that issues are organized around internal components rather than demonstrable outcomes.

Use a GitHub Project when priority, status, and blocked work need to be visible together. Introduce a milestone only
when accepted issues genuinely belong to a planned release or delivery outcome; it is not a second status board.
