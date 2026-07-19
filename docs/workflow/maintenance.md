---
icon: lucide/package-check
---

# Maintenance and releases

!!! note "Pain point"

    A project can continue adding features while dependencies age, documentation drifts, defects recur, and unused
    flexibility remains in the codebase. Delivery speed then creates a growing maintenance burden.

Maintenance begins with the first merged change. It includes dependency updates, defects, compatibility,
documentation accuracy, security response, and removal of obsolete behavior. It is not a separate phase that begins
after feature development; it is the work required to keep existing promises true.

## Observe and maintain

Treat failures and user reports as new inputs to the development loop. Diagnose before changing code, distinguish
symptoms from causes, and keep fixes narrow. A recurring failure is evidence that the project may need a stronger
test, clearer instruction, safer default, or automated constraint—not merely another manual repair.

Periodically review:

- whether setup instructions still work from a clean environment;
- whether dependencies and Actions remain supported and trustworthy;
- whether checks still protect real risks without creating avoidable friction;
- whether documentation describes current behavior; and
- whether configuration, compatibility paths, or abstractions are no longer used.

Remove code and configuration that no longer serve a supported behavior. Unused flexibility is still maintenance
work because contributors must continue to understand and preserve it.

Dependabot can propose routine dependency updates, but maintainers must review release notes, compatibility, and
verification evidence. Automation creates a candidate change, not an approval. Grouped updates reduce noise, but a
failed group may need to be separated to identify the incompatible dependency.

## Decide when to release

Release when the main branch contains a coherent, verified outcome worth communicating or distributing. Do not release merely because a calendar interval elapsed unless the project has intentionally adopted scheduled releases.

Before a release, confirm that required checks pass, user-facing documentation matches behavior, known limitations
are recorded, versioning communicates compatibility, and rollback or recovery is understood where relevant. A
release should tell users what changed and whether they must take action; a Git tag alone does not provide that
context.

The template does not prescribe a release mechanism because packaging and deployment are project-specific. Add one only after the product, distribution channel, and versioning policy are known.
