---
icon: lucide/box
---

# Dev container

The dev container answers one question: **where does development happen?**

```mermaid
flowchart LR
    H[Host] --> C[Linux container]
    C --> S[Post-create setup]
    S --> M[Mise install]
    M --> W[Ready workspace]
```

## What belongs in the image

The Dockerfile contains operating-system dependencies and bootstrap tools: Mise, uv, Python, and tmux. These are required before project-level tools can be installed.

## What stays outside the image

Linters, formatters, runtimes, and project commands belong in Mise. Keeping them in `mise.toml` makes them visible, replaceable, and available outside the container where supported.

## Creation lifecycle

`devcontainer.json` builds the Dockerfile, forwards the optional `MISE_GITHUB_TOKEN`, and runs `scripts/setup.sh`. That script moves to the repository root, trusts `mise.toml`, and installs the declared tools.

Rebuild the container when its Dockerfile or container configuration changes. Run `mise install` when only project tools change.

## Trade-off

The container adds Docker overhead and requires a rebuild for system-level changes. It provides a consistent Linux reference across Windows, macOS, and Linux hosts, which is more valuable for this template than perfect native parity.

## Official documentation

- [Development Containers specification](https://containers.dev/)
- [VS Code Dev Containers documentation](https://code.visualstudio.com/docs/devcontainers/containers)
- [Dockerfile reference](https://docs.docker.com/reference/dockerfile/)
- [Docker Desktop documentation](https://docs.docker.com/desktop/)
