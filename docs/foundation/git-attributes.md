---
icon: lucide/git-branch
---

# Git attributes

!!! note "Pain point"

    Git can check out text differently according to operating-system and user configuration. Line endings may be
    rewritten unexpectedly, and binary files can appear as meaningless text changes.

`.gitattributes` tells Git how to classify tracked files and normalize their content. Unlike editor settings, these rules participate in checkout, staging, diffs, and generated archives.

## What this repository declares

| Category | Behavior |
| --- | --- |
| General text | Automatically detected and normalized in Git |
| Documentation and structured text | Treated as text, with useful diff drivers where available |
| Unix scripts and container files | Stored and checked out with LF |
| Batch, CMD, and PowerShell scripts | Stored as text and checked out with CRLF |
| Images and archives | Treated as binary |
| Patch files | Left untouched so exact line endings are preserved |
| Repository metadata | Excluded from generated Git archives where configured |

## Why it matters

Without repository attributes, a contributor's `core.autocrlf` and operating system can rewrite line endings differently. Binary files may also appear as meaningless textual diffs. Explicit attributes make Git behavior part of the repository rather than personal machine state.

## Relationship to other files

- `.editorconfig` guides the editor before Git sees a change.
- `.gitattributes` defines Git's tracked representation and checkout behavior.
- `prek` detects mixed endings and other problems before Git operations complete.

Inspect effective attributes with:

```bash
git check-attr -a -- scripts/setup.sh
git check-attr -a -- scripts/enter_project.ps1
```

After intentionally changing normalization rules, use `git add --renormalize .` and review the complete diff before committing. See the official [gitattributes documentation](https://git-scm.com/docs/gitattributes).
