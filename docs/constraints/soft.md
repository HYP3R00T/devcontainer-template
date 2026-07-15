---
icon: lucide/clipboard-check
---

# Soft constraints

Soft constraints govern decisions requiring context. They are expressed through contribution guidance, issue and pull-request templates, review standards, and concise agent instructions.

Examples include:

- understand and be able to explain everything submitted;
- keep a change focused on its approved issue;
- prefer the smallest complete solution;
- avoid speculative abstractions and unrelated refactoring;
- document behavior that users or maintainers must know; and
- stop and discuss a material change in scope.

## How they are upheld

A template can request evidence and make expectations visible, but it cannot prove that a contributor understands the code or that an architecture is appropriate. Maintainers uphold these constraints during issue refinement and pull-request review. Rejection is a valid enforcement outcome even though the judgment is human.

AI-assisted work follows the same standard. The person submitting the change owns its correctness and must be able to maintain it without the generating agent.
