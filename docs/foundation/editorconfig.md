---
icon: lucide/panel-top
---

# Consistent editing with EditorConfig

!!! note "Pain point"

    Editors use different defaults for indentation, encoding, line endings, trailing spaces, and final newlines.
    Those differences create noisy reviews even when contributors change the same logical content.

EditorConfig gives compatible editors a shared baseline for how files are created and saved. It reduces noisy diffs caused by contributors using different editor defaults.

The repository's `.editorconfig` is discovered automatically when an editor opens a file. `root = true` tells the editor to stop searching parent directories, preventing unrelated machine-level configuration from changing this project.

## Repository defaults

| Files | Applied behavior |
| --- | --- |
| All files | UTF-8, LF, final newline, trimmed trailing whitespace, spaces, two-space indentation, and a 120-character line-length preference |
| Markdown | Four-space indentation for nested Markdown content |
| Batch, CMD, and PowerShell | CRLF line endings |
| Dockerfile | Four-space indentation |

`max_line_length` is an editor hint; support varies between editors and it is not a hard repository check.

## Why it helps

- New files begin with predictable encoding and line endings.
- Tabs and spaces do not change with personal editor settings.
- Files end cleanly with one newline and no accidental trailing spaces.
- Windows scripts retain their expected CRLF endings while the rest of the repository defaults to LF.
- Formatting changes stay focused on meaningful content.

The dev container installs the [EditorConfig extension for VS Code](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig). Other editors may support EditorConfig directly or through a plugin; consult the official [EditorConfig editor list](https://editorconfig.org/#pre-installed).

## VS Code workspace settings

The repository's `.vscode/settings.json` adds editor-specific behavior that EditorConfig cannot express:

| Setting | Selected behavior | Why it is configured |
| --- | --- | --- |
| `editor.formatOnSave` | Enabled | Applies the selected formatter before routine edits leave the editor |
| `editor.insertSpaces` | Enabled | Keeps VS Code's indentation behavior aligned with EditorConfig |
| Markdown formatter | Rumdl | Uses the same Markdown tool configured by the repository and Git hook |
| TOML formatter | Even Better TOML | Gives Mise, Zensical, and rumdl configuration a syntax-aware formatter |
| YAML formatter | Red Hat YAML | Provides syntax-aware formatting for workflows and issue forms |
| YAML quick suggestions | Enabled outside comments | Preserves schema-assisted completion without suggesting text inside comments |

These settings are workspace recommendations, not CI enforcement. The corresponding extensions are installed by
the Dev Container configuration so the documented defaults are available in the reference environment.

## Responsibility boundaries

EditorConfig influences editing, but it is not enforcement by itself. A contributor can use an unsupported editor or disable its integration.

| Layer | Responsibility |
| --- | --- |
| `.editorconfig` | Guide compatible editors while files are being changed |
| `.gitattributes` | Normalize text when Git checks files in and out |
| `prek` | Detect or repair repository-level problems before Git operations complete |
| Language formatters | Apply syntax-aware formatting rules |

Keep these layers aligned, but do not force each one to duplicate every rule. See the official [EditorConfig specification](https://spec.editorconfig.org/) for property and matching semantics.
