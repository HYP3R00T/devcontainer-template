---
icon: lucide/route
---

# Traceability

!!! note "Pain point"

    Code shows the implementation that survived, but it rarely explains the request, rejected alternatives, review
    evidence, or operational constraints. Preserving every conversation creates the opposite problem: too much
    history to find the decisions that matter.

Traceability should let a future maintainer answer four questions without reconstructing an entire conversation:

1. What pain point or request started the work?
2. Why was this scope accepted?
3. Where was it implemented and reviewed?
4. What evidence supported integration?

| Record | What it should preserve |
| --- | --- |
| Issue | Proposal, accepted scope, criteria, priority, dependencies, and relevant exploration |
| Branch | Temporary workspace for one issue |
| Pull request | Implementation summary, review, verification, and integration decision |
| Commit history | Meaningful steps in the accepted implementation |
| Code and current documentation | The behavior that exists now |

Link these records instead of copying their complete contents. Close an issue through its pull request, reference decisions where they affect implementation, and create follow-up issues for deferred work.

A practical chain looks like this:

```text
Project item → issue → branch → pull request → commits → current documentation
```

Not every link must be typed manually. GitHub can connect branches, pull requests, closing keywords, and issues,
but the contributor should verify that a reader can move from the current change back to its accepted reason.

## When an issue is not enough

Most implementation decisions belong in the issue or pull request because their relevance ends with that change.
A durable decision deserves current project documentation when it establishes a boundary that future work must
continue to respect—for example, an architectural style, compatibility promise, data-ownership rule, or choice
that rejected plausible alternatives.

Some projects preserve those decisions as Architecture Decision Records. This template does not create an ADR
folder because not every derived project needs that process. Add one when consequential architectural decisions
recur and the team is willing to maintain the records. The important distinction is durability, not the document
name: temporary implementation reasoning stays with the change; ongoing constraints must be discoverable from the
current documentation.

Do not preserve every thought. Record decisions that influenced the result, rejected alternatives likely to be
reconsidered, and constraints a future maintainer could otherwise violate unknowingly. Git history is an audit
trail, not a replacement for clear current documentation. When behavior changes, update the current explanation;
do not force readers to infer the present from a sequence of old pull requests.
