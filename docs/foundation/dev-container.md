---
icon: lucide/box
---

# Dev Container

!!! note "Pain point"

    Development directly on Windows, macOS, and Linux produces different paths, shells, native packages, line
    endings, and tool behavior. Each environment can be configured successfully, but maintaining equivalent setup
    across every machine consumes time and makes failures harder to reproduce.

This template uses a Linux Dev Container as its reference development environment. Contributors may use different
host operating systems, but the project runs inside the same defined environment when platform behavior matters.

## Selected design

| File | Responsibility | Why it is separate |
| --- | --- | --- |
| `.devcontainer/Dockerfile` | Define the operating system, native packages, and bootstrap binaries | Image-level requirements can be cached and rebuilt consistently |
| `.devcontainer/devcontainer.json` | Tell compatible editors how to build and enter the environment | Editor integration remains declarative and easy to inspect |
| `scripts/setup.sh` | Initialize the mounted repository after creation | Repository-dependent setup cannot run before the workspace is available |
| `mise.toml` | Install project tools and expose shared commands | Tool choices remain visible and usable outside the image where supported |

The Dockerfile uses Microsoft's Ubuntu Dev Container base and runs as its provided development user. It installs
Python and tmux as operating-system packages, then copies Mise and uv from their published container images.

Python supports Python-based hook environments and repository utilities, while `uvx` runs tools such as Zensical
in isolated environments. Its presence does not make the eventual application a Python project. Mise, uv, and
their source images intentionally track current releases; the template prefers a current development baseline over
byte-for-byte historical rebuilds.

## Creation lifecycle

```text
Host opens repository
→ Dev Container builds the Dockerfile
→ workspace is mounted
→ postCreateCommand runs scripts/setup.sh
→ setup trusts mise.toml and installs locked tools
→ Mise project-entry automation configures local Git tooling
→ workspace is ready
```

`devcontainer.json` forwards the optional `MISE_GITHUB_TOKEN` from the host. Mise can use it for authenticated
GitHub downloads and avoid anonymous API rate limits. The token is optional and must never be committed.

Rebuild the container when the Dockerfile or `devcontainer.json` changes. Run `mise install` when only project tools
change; rebuilding the complete image would add time without changing the image itself.

## What consistency it provides

- One Linux reference for shells, paths, native packages, and executable behavior.
- A version-controlled machine definition instead of personal setup notes.
- The same onboarding path on supported Windows, macOS, and Linux hosts.
- A clear boundary between operating-system packages and project tools.

The container does not make host behavior identical. Docker, filesystem performance, networking, credentials, and
hardware still originate outside it. Native development remains possible, but disagreements are resolved against
the container because it is the documented reference.

## Verify and adapt

After opening the container, verify the environment with:

```bash
mise doctor
mise ls --current
prek run --all-files
```

Add an operating-system package to the Dockerfile only when it is required before project tools can operate. Add
runtimes, linters, and recurring project commands through Mise. Keep post-create work idempotent and limited to
repository initialization.

## Official documentation

- [Development Containers specification](https://containers.dev/)
- [VS Code Dev Containers documentation](https://code.visualstudio.com/docs/devcontainers/containers)
- [Dockerfile reference](https://docs.docker.com/reference/dockerfile/)
- [Docker Desktop documentation](https://docs.docker.com/desktop/)
