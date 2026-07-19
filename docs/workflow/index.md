---
icon: lucide/repeat-2
---

# Development workflow

!!! note "Pain point"

    Moving directly from an idea to a large implementation hides assumptions, produces changes that are difficult
    to review, and leaves little evidence explaining why the resulting system exists.

Software development is a repeated decision cycle, not a single request followed by a large implementation. The
cycle applies whether the work is performed manually, with an AI agent, or through a mixture of both. Tools may
accelerate implementation, but they do not remove the need to establish intent, review evidence, and decide what
enters the maintained system.

```text
Problem → decision → issue → small change → verification → review → integration → observation
   ↑                                                                          │
   └────────────────────────────── learning ──────────────────────────────────┘
```

Every pass through the cycle should produce one understandable increment. If the scope cannot be reviewed
comfortably, split it before implementation rather than explaining a large change afterward.

## The records have different jobs

| Record | Question it answers |
| --- | --- |
| Proposal or issue | What pain point are we addressing, and what outcome have we accepted? |
| GitHub Project | Which accepted work matters now, and what is blocked? |
| Branch | Where is one increment being developed without destabilizing the default branch? |
| Commits | What coherent implementation steps were taken? |
| Pull request | Does the result satisfy the issue, and what evidence supports integration? |
| Current code and documentation | What is true after the change is integrated? |

These are not duplicate containers for the same text. Link them and let each preserve the information needed at
its stage. A solo maintainer benefits from the same separation: it creates a pause between proposing work and
accepting its implementation without requiring meetings or heavyweight process.

## Operating rules

- Do not begin implementation until the problem and success condition are clear enough to review.
- Use one issue as the unit of accepted work and one pull request as its implementation record.
- Record uncertainty before code; record implementation evidence in the pull request.
- Keep the main branch releasable and integrate only after required checks pass.
- Observe completed work and feed defects or new understanding back into the issue queue.

The rules describe a default rhythm, not an excuse for ceremony. A typo may need only a concise issue and pull
request; a risky architectural change needs more exploration and evidence. Increase the depth of the record when
the cost of misunderstanding increases.

First understand [hard and soft constraints](constraints.md). Then continue with
[Start a project](start-project.md) and [Iterative development](iteration.md).
