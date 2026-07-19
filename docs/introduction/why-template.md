---
icon: lucide/compass
---

# Why this template exists

!!! note "Pain point"

    A new project often begins by rebuilding the same development machinery: selecting a reference environment,
    installing tools, normalizing files, configuring checks, and explaining contribution expectations. Repeating
    that work costs time and produces small differences that become maintenance problems later.

The template provides one understandable baseline that works for humans, automation, and AI-assisted development.
A newcomer should be able to enter a known environment, run the same checks as CI, and trace each behavior to a
version-controlled file or an explicitly documented GitHub setting.

## Design principles

- **Environment before application:** stabilize where work happens before writing product code.
- **Configuration over memory:** declare tools and shared behavior in version-controlled files.
- **Shared entry points:** humans, agents, Git hooks, and CI should call the same commands where practical.
- **Safe repetition:** setup and project-entry actions must be idempotent.
- **Small baseline:** provide language-agnostic needs and add project-specific choices only when they become real.
- **Human ownership:** generated or automated work must remain inspectable, explainable, and replaceable.

## What the template does not decide

It does not choose an application architecture, programming language, test strategy, release mechanism, or
deployment platform. Those decisions depend on the product. Empty placeholders for them would look complete while
providing no real protection.

## Trade-off

Containers, tool managers, hooks, and documentation introduce configuration that must be maintained. In return,
the project gains consistent onboarding, visible decisions, repeatable checks, and fewer machine-specific failures.
The baseline is deliberately opinionated, but every part should be removable when a derived project no longer
benefits from it.
