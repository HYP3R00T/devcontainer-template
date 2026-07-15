---
icon: lucide/repeat-2
---

# Development workflow

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

Continue with [Start a project](start-project.md), then [Iterative development](iteration.md).
