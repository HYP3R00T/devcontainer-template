# Custom Instructions for Commit Message Generation

Follow the Conventional Commits format for all commit messages:

**Format**: `<type>(<scope>): <subject>`

Where:
- `<type>`: One of `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`, `perf`
- `<scope>`: Optional, used to indicate which area of the project is affected
- `<subject>`: Brief description of the change in imperative mood

## Guidelines

- Keep the subject line under 50 characters.
- Start the subject with a verb in imperative mood (e.g., "add", "fix", "update", "remove").
- Use lowercase for the subject line.
- For significant changes, provide a detailed description in the body.
- Reference related issues or pull requests in the footer using `Closes #123` or `Fixes #456`.

## Examples

- `feat: add user authentication module`
- `fix: resolve timeout issue in API calls`
- `docs: update installation instructions`
- `refactor: simplify data validation logic`
- `test: add unit tests for payment module`
- `chore: update dependencies`
