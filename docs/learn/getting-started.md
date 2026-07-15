---
icon: lucide/rocket
---

# Getting started

## What you need

Install these host tools before opening the repository:

| Tool | Why it is needed | Official instructions |
| --- | --- | --- |
| Git | Clone and version the repository | [Install Git](https://git-scm.com/downloads) |
| Docker Desktop | Build and run the Linux development container | [Install Docker Desktop](https://docs.docker.com/desktop/) |
| Visual Studio Code | Open and control the development workspace | [Download VS Code](https://code.visualstudio.com/download) |
| Dev Containers extension | Connect VS Code to the container | [Install the extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) |

If dev containers are new to you, complete the official [Dev Containers tutorial](https://code.visualstudio.com/docs/devcontainers/tutorial). Windows users should also follow Microsoft's [WSL installation guide](https://learn.microsoft.com/windows/wsl/install); Docker Desktop should use its WSL 2 backend.

Start Docker Desktop before opening the project. You can verify the command-line prerequisites with:

```bash
git --version
docker version
code --version
```

## Open the project

1. Create a repository from this template and clone it.
2. Optionally define `MISE_GITHUB_TOKEN` on the host to avoid anonymous GitHub rate limits during the first build.
3. Open the repository in Visual Studio Code.
4. Choose **Dev Containers: Reopen in Container**.
5. Wait for the post-create setup to finish.

The setup trusts this repository's Mise configuration and installs its declared tools. The enter hook then makes Commitizen available and configures the Git hooks.

## Verify the environment

```bash
mise doctor
mise ls --current
mise tasks
prek run --all-files
```

## Adapt it to your project

Add the project's runtime and language-specific tools, ignore rules, checks, and CI tasks. Keep shared commands behind Mise tasks so contributors and CI use the same interface.

Read [Dev container](../concepts/dev-container.md) and [Mise](../concepts/mise.md) before changing the baseline.
