---
icon: lucide/repeat-2
---

# Development workflow

!!! note "Pain point"

    Moving directly from an idea to a large implementation hides assumptions, produces changes that are difficult
    to review, and leaves little evidence explaining why the resulting system exists.

Software development is a repeated decision cycle, not a single request followed by a large code generation.

```text
Problem → decision → issue → small change → verification → review → integration → observation
   ↑                                                                          │
   └────────────────────────────── learning ──────────────────────────────────┘
```

Every pass through the cycle should produce one understandable increment. If the scope cannot be reviewed comfortably, split it before implementation rather than explaining a large change afterward.

## Operating rules

- Do not begin implementation until the problem and success condition are clear enough to review.
- Use one issue as the unit of accepted work and one pull request as its implementation record.
- Record uncertainty before code; record implementation evidence in the pull request.
- Keep the main branch releasable and integrate only after required checks pass.
- Observe completed work and feed defects or new understanding back into the issue queue.

First understand [hard and soft constraints](constraints.md). Then continue with
[Start a project](start-project.md) and [Iterative development](iteration.md).
