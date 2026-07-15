---
icon: lucide/package-check
---

# Maintenance and releases

Maintenance begins with the first merged change. It includes dependency updates, defects, compatibility, documentation accuracy, security response, and removal of obsolete behavior.

## Observe and maintain

Treat failures and user reports as new inputs to the development loop. Diagnose before changing code, distinguish symptoms from causes, and keep fixes narrow. Remove code and configuration that no longer serve a supported behavior; unused flexibility is still maintenance work.

Dependabot can propose routine dependency updates, but maintainers must review compatibility and verification evidence. Automation creates a candidate change, not an approval.

## Decide when to release

Release when the main branch contains a coherent, verified outcome worth communicating or distributing. Do not release merely because a calendar interval elapsed unless the project has intentionally adopted scheduled releases.

Before a release, confirm that required checks pass, user-facing documentation matches behavior, known limitations are recorded, versioning communicates compatibility, and rollback or recovery is understood where relevant.

The template does not prescribe a release mechanism because packaging and deployment are project-specific. Add one only after the product, distribution channel, and versioning policy are known.
