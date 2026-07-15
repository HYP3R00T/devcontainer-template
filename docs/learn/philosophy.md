---
icon: lucide/compass
---

# Why this template exists

A project should begin with its problem—not with every contributor rebuilding the same development setup.

## Objective

Create one understandable baseline that works for humans, automation, and AI agents. A newcomer should be able to clone the repository, enter a known environment, run the same commands as CI, and understand where each behavior comes from.

## Principles

- **Environment before application:** stabilize where work happens before writing product code.
- **Configuration over memory:** declare tools and commands in version-controlled files.
- **One public workflow:** humans, agents, and CI should use the same entry points.
- **Safe repetition:** setup and hooks must be idempotent.
- **Small baseline:** include what every project needs; add language-specific choices later.
- **Human ownership:** automation may accelerate work, but it must remain inspectable and replaceable.

## The trade-off

Containers and tool managers add configuration. In return, the project gains repeatability, easier onboarding, and fewer machine-specific failures. Native environments remain possible, but the dev container is the reference when platforms disagree.

This template is not an application architecture or a complete delivery process. It is the stable ground on which those decisions can be made deliberately.
