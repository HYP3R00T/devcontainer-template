<!-- rumdl-disable MD041 -->

<div align="center">

# DevContainer Template

A minimal, reusable foundation for consistent development environments and maintainable project workflows.

[Documentation](https://hyp3r00t.github.io/devcontainer-template/) · [Use this template](https://github.com/HYP3R00T/devcontainer-template/generate) · [Contributing](CONTRIBUTING.md)

[![Quality Gate](https://img.shields.io/github/actions/workflow/status/HYP3R00T/devcontainer-template/ci.yaml?branch=main&style=for-the-badge&label=Quality%20Gate&logo=githubactions)](https://github.com/HYP3R00T/devcontainer-template/actions/workflows/ci.yaml)
[![License: MIT](https://img.shields.io/github/license/HYP3R00T/devcontainer-template?style=for-the-badge&label=License)](LICENSE)

</div>

<!-- Add a project screenshot or demonstration here. -->

## About

This repository provides a language-agnostic starting point for projects that need a predictable Linux development environment across Windows, macOS, and Linux hosts. The Dev Container supplies the environment, while Mise provides a shared interface for installing and running project tools.

The template also establishes repository hygiene, automated checks, contribution expectations, and documentation publishing without choosing a programming language or application architecture. Derived projects can add only the runtimes and checks they actually need.

## Features

- Reproducible development through a Docker-based Dev Container.
- Cross-platform project entry scripts for Unix-like systems and Windows.
- Tool and task management with [Mise](https://mise.jdx.dev/).
- Local Git hooks and repository checks powered by [prek](https://prek.j178.dev/).
- A pull-request quality gate that runs the same checks as local development.
- Structured issue forms, contribution guidance, security reporting, and code ownership.
- Developer documentation published with [Zensical](https://zensical.org/).
- Automated GitHub Actions dependency updates through Dependabot.

## Use this template

1. Select [**Use this template**](https://github.com/HYP3R00T/devcontainer-template/generate) and create a repository.
2. Open the new repository in Visual Studio Code.
3. Run **Dev Containers: Reopen in Container** from the Command Palette.
4. Wait for the setup to install the declared tools and configure the Git hooks.
5. Add the runtimes, dependencies, checks, and tasks required by the project.

For environment requirements and verification commands, read the [documentation](https://hyp3r00t.github.io/devcontainer-template/).

## Contributing

Contributions are welcome when they are focused, understandable, and maintainable. Read [CONTRIBUTING.md](CONTRIBUTING.md) before proposing a change.

## License

This project is available under the [MIT License](LICENSE).

<div align="center">

Developed with ❤️ by [HYP3R00T](https://github.com/HYP3R00T)

</div>
