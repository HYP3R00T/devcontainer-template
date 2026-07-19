---
icon: lucide/route
---

# Traceability

!!! note "Pain point"

    Code shows the implementation that survived, but it rarely explains the request, rejected alternatives, review
    evidence, or operational constraints. Preserving every conversation creates the opposite problem: too much
    history to find the decisions that matter.

Traceability should answer: what was requested, why was it accepted, how was it implemented, and what evidence supported integration?

| Record | What it should preserve |
| --- | --- |
| Issue | Proposal, accepted scope, criteria, priority, dependencies, and relevant exploration |
| Branch | Temporary workspace for one issue |
| Pull request | Implementation summary, review, verification, and integration decision |
| Commit history | Meaningful steps in the accepted implementation |
| Code and current documentation | The behavior that exists now |

Link these records instead of copying their complete contents. Close an issue through its pull request, reference decisions where they affect implementation, and create follow-up issues for deferred work.

Do not preserve every thought. Record decisions that influenced the result, rejected alternatives likely to be reconsidered, and constraints a future maintainer could otherwise violate unknowingly. Git history is an audit trail, not a replacement for clear current documentation.
