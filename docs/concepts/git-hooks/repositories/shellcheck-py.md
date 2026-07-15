---
icon: lucide/terminal-square
---

# shellcheck-py

Official source: [shellcheck-py/shellcheck-py](https://github.com/shellcheck-py/shellcheck-py)

The provider packages ShellCheck so the hook can run in an isolated environment. The configured `shellcheck` hook analyzes supported shell scripts before they are committed.

## Why it is included

Shell scripts bootstrap the development environment. A quoting, expansion, portability, or error-handling mistake can break onboarding for every contributor. Static analysis catches many of these failures without executing the script.

## Failure and resolution

ShellCheck reports a line and an `SC` rule code. Read the diagnostic and its linked rule explanation, then correct the script. Suppress a rule only when the behavior is deliberately safe and the reason is documented next to the suppression.

```bash
prek run shellcheck --all-files
shellcheck scripts/setup.sh scripts/enter_project.sh
```

The [ShellCheck project](https://www.shellcheck.net/) provides the analyzer documentation and searchable rule explanations.
