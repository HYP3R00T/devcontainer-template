---
icon: lucide/sprout
---

# Start a project

!!! note "Pain point"

    Beginning with technology or generated code can produce a functioning solution before anyone has agreed on the
    user, desired outcome, success evidence, or boundaries. The project then accumulates code without clear intent.

The first product artifact is a clear problem statement, not application code. This does not require a lengthy
product specification. It requires enough shared context that another person—or the same maintainer several weeks
later—can tell what outcome is being pursued and what would count as success.

## Establish direction

Write down:

1. Who experiences the problem?
2. What happens today?
3. What outcome should improve?
4. What evidence would show that the solution works?
5. Which boundaries, risks, and assumptions are already known?

For a solo project, this can begin as one concise feature-proposal issue. Refine an uncertain direction in that
issue until the outcome is concrete enough to approve or decline.

A useful statement describes observable reality rather than prescribing a favorite implementation. For example,
“new contributors cannot verify their setup consistently” leaves room to compare solutions. “Add script X” has
already selected a solution and may hide the reason it is needed.

## Decide whether the work is ready

An issue is ready for implementation when:

- the affected person or system is identifiable;
- the desired outcome can be demonstrated or checked;
- important exclusions prevent obvious scope expansion;
- unresolved questions are small enough to answer during implementation; and
- the work is not blocked by an earlier decision or change.

Acceptance criteria should describe outcomes, not a transcript of anticipated code edits. They create a stable
review boundary while leaving implementation details open to investigation.

## Shape the first increment

Choose the smallest end-to-end result that can test an important assumption. “End-to-end” means the increment is
usable or observable at its boundary; it does not mean completing every feature around it. Break larger work into
issues whose outcomes can be demonstrated independently. Record dependencies only when one issue genuinely cannot
succeed before another.

Add issues to a GitHub Project when their priority, dependencies, and state need to be visible together. Avoid
milestones until the project has a real release or delivery plan that needs them.

Only after this should the project add its language, application structure, and project-specific checks to the
foundation. Those choices should follow from the first real increment instead of becoming speculative template
work.
