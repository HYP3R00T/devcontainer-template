# Contributing

Thank you for taking the time to improve this project. Contributions are welcome when they are focused, understandable, and aligned with the project's direction.

## The responsibility rule

You must understand everything you submit.

Using AI tools to explore ideas, write code, create tests, or prepare documentation is welcome. However, the contributor—not the tool—is responsible for the final change. You must be able to explain:

- what the change does and why it is needed;
- how it fits the existing design;
- which relevant edge cases were considered; and
- how the change was verified.

A maintainer may ask about any part of a contribution during review. A pull request that the contributor cannot reasonably explain will not be merged and may be closed. Passing automated checks does not replace understanding or ownership.

## Before starting

Search the existing issues before beginning work.

- Use the appropriate issue form for a reproducible bug or feature proposal.
- Refine unclear or significant proposals with the maintainer in the issue before implementation.
- Wait for maintainer agreement before investing in a substantial change.
- Small corrections, such as an obvious documentation typo, may be submitted directly.

Agreement to begin work does not grant repository access or guarantee that the result will be merged. External
contributors should work from a fork; collaborator access is reserved for maintainers with ongoing repository
responsibilities.

Keeping the scope agreed in advance prevents duplicated work and makes reviews faster.

## Set up the project

Install [Git](https://git-scm.com/downloads), [Docker Desktop](https://docs.docker.com/desktop/), [Visual Studio Code](https://code.visualstudio.com/download), and the [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers). Start Docker Desktop before opening the project. Windows users should use Docker Desktop with its WSL 2 backend.

1. Fork the repository, or clone it directly if you have write access.
2. Clone the repository and open it in Visual Studio Code.
3. Run **Dev Containers: Reopen in Container** from the Command Palette.
4. Wait for the container setup to install the tools and configure the Git hooks.
5. Verify the development environment:

   ```bash
   mise doctor
   mise ls --current
   prek run --all-files
   ```

6. Create a branch from the latest `main` branch.

   ```bash
   git switch -c <type>/<short-description>
   ```

   Common types include `feat`, `fix`, `docs`, `test`, `refactor`, and `chore`.

## Make a focused change

- Address one problem per pull request.
- Prefer the smallest complete solution that satisfies the agreed requirement.
- Follow the existing structure, naming, and style.
- Avoid unrelated formatting, refactoring, dependency, or generated-file changes.
- Add or update tests when behavior changes and the project provides a test suite.
- Update documentation when setup, behavior, interfaces, or contributor workflows change.
- Never include credentials, tokens, private data, or unrelated machine-generated files.

Comments and documentation should explain intent, constraints, or non-obvious decisions. Do not restate code that is already clear.

## Verify the change

Run the repository checks before pushing:

```bash
prek run --all-files
```

Also run any language-specific tests, builds, or checks documented by the project. Do not bypass failing hooks or disable checks to make a contribution pass.

## Write clear commits

This project follows [Conventional Commits](https://www.conventionalcommits.org/):

```text
<type>(<optional-scope>): <short description>
```

Keep commits understandable and free from unrelated changes. Examples include `fix: handle missing configuration` and `docs: clarify container setup`.

## Open a pull request

Complete the pull request template and include:

- the related issue, when applicable;
- a concise explanation of what changed and why;
- the verification you performed;
- any relevant risks, limitations, or follow-up work; and
- the documentation impact.

Keep the pull request current, respond to review questions, and ensure the required CI checks pass. Review feedback is part of the contribution process; approval and merge remain at the maintainers' discretion.

For pull requests from external forks, GitHub Actions may wait for a maintainer to inspect the changes and approve
the workflow run. That approval permits CI execution only; it is not approval of the contribution itself.

## Security and community

Do not report security vulnerabilities in a public issue. Follow the private reporting instructions in [Security Policy](SECURITY.md).

All participation must follow the [Code of Conduct](.github/CODE_OF_CONDUCT.md).

## License

By contributing, you agree that your contribution will be licensed under the same terms as this project. See [LICENSE](LICENSE).

## Thank you

Thoughtful contributions make a project stronger. Whether you improve code, tests, documentation, or an idea, thank you for bringing care, curiosity, and ownership to the work.
