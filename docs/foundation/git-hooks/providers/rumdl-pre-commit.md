---
icon: lucide/file-text
---

# rumdl-pre-commit

!!! note "Pain point"

    Markdown can render successfully while remaining inconsistent, difficult to review, or incompatible with the
    published documentation style. Manual proofreading does not reliably catch structural issues across every page.

Official source: [rvben/rumdl-pre-commit](https://github.com/rvben/rumdl-pre-commit)

The provider packages rumdl for an isolated hook environment. The configured `rumdl` hook checks Markdown files and reads the project policy from `rumdl.toml`.

## Why it is included

Documentation is a published output of this template, not incidental prose. Consistent Markdown improves GitHub rendering, the Zensical site, reviews, and future maintenance. Using the same configuration locally and in the hook prevents editor-specific style from becoming repository policy.

## Failure and resolution

A failure reports a Markdown rule, file, and location. Correct the content based on the diagnostic. When a rule is safely fixable, use:

```bash
rumdl check --fix <path>
prek run rumdl --all-files
```

Do not disable a rule merely because existing prose violates it. Decide whether the rule conflicts with the documentation style, document that decision in `rumdl.toml`, and keep the exception narrow.

The main [rumdl documentation](https://rumdl.dev/) explains rules, configuration, formatting, and command-line behavior.
