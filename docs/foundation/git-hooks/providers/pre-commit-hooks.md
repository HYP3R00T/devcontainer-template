---
icon: lucide/list-checks
---

# pre-commit-hooks

!!! note "Pain point"

    Small repository defects—invalid configuration, unsafe filenames, broken executable metadata, conflict markers,
    and accidental secrets—are easy to miss individually but expensive once they enter shared history.

Official source: [pre-commit/pre-commit-hooks](https://github.com/pre-commit/pre-commit-hooks)

This upstream repository supplies small, language-agnostic checks. They are grouped here by the problem they prevent rather than presented as an unexplained flat list.

## Structured-file validity

| Hook | What it checks | Why it is included |
| --- | --- | --- |
| `check-json` | Parses JSON files | Prevents broken editor, tool, and API configuration |
| `check-toml` | Parses TOML files | Protects Mise, Zensical, rumdl, and future tool configuration |
| `check-yaml` | Parses YAML with a safe loader | Prevents invalid GitHub workflows, templates, and hook configuration |

A failure identifies a file that cannot be parsed. Correct the syntax at the reported location; do not weaken the parser merely to silence a portability problem.

## Cross-platform filesystem safety

| Hook | What it checks | Why it is included |
| --- | --- | --- |
| `check-case-conflict` | Paths that differ only by case | Case-insensitive Windows and macOS filesystems cannot represent both safely |
| `check-illegal-windows-names` | Reserved or invalid Windows paths | Keeps avoidable filename failures out of clones and archives |
| `check-executables-have-shebangs` | Executable text files declare an interpreter | Makes direct execution unambiguous |
| `check-shebang-scripts-are-executable` | Shebang scripts have the Git executable bit | Preserves execution on Unix, in containers, and in CI |
| `destroyed-symlinks` | Symlinks accidentally materialized as regular files | Prevents Windows checkout limitations from corrupting repository structure |

Filename failures require a rename. Executable failures require either the correct shebang or an intentional Git mode change with `git update-index --chmod=+x` or `--chmod=-x`. A destroyed symlink should be restored from Git in an environment with symlink support.

## Text hygiene

| Hook | What it does | Failure behavior |
| --- | --- | --- |
| `end-of-file-fixer` | Ensures exactly one final newline | Modifies the file; review and stage the fix |
| `mixed-line-ending` | Rejects a mixture of LF and CRLF within one file | Reports the file; normalize it according to `.gitattributes` |
| `trailing-whitespace` | Removes spaces and tabs at line ends | Modifies the file; review and stage the fix |

The mixed-line-ending hook uses `--fix=no`. It detects inconsistency without overriding the repository policy: Unix-oriented text uses LF, while Windows scripts intentionally use CRLF.

## Repository protection

| Hook | What it checks | Why it is included |
| --- | --- | --- |
| `check-added-large-files` | Newly added files above the default size threshold | Keeps unsuitable binaries and generated artifacts out of normal Git history |
| `check-merge-conflict` | Unresolved conflict markers | Prevents accidental commits of incomplete merges |
| `detect-private-key` | Recognizable private-key material | Stops one important class of secret exposure before it enters history |
| `no-commit-to-branch` | Direct commits to `main` and `master` | Requires development branches and pull-request integration |

A large file should be removed, stored elsewhere, or handled through an explicitly adopted Git LFS policy. Merge markers must be resolved. A detected key must be removed and rotated if exposure was possible. A protected-branch failure means the work belongs on a separate branch.

## Running these hooks

```bash
prek run check-yaml --all-files
prek run trailing-whitespace --all-files
prek run no-commit-to-branch
```

The upstream [hook reference](https://github.com/pre-commit/pre-commit-hooks#hooks-available) documents every available hook and option. This template selects only checks that apply to its current language-agnostic contents.
