# Contributing to This Project

Thank you for your interest in contributing! This document provides guidelines and instructions for contributing.

## Code of Conduct

Please review our [Code of Conduct](/.github/CODE_OF_CONDUCT.md). All contributors are expected to uphold this code in all community interactions.

## Getting Started

### Prerequisites

- Git installed and configured
- A GitHub account
- Development environment set up (see [README.md](README.md))

### Setting Up Your Development Environment

1. **Fork the repository** on GitHub
2. **Clone your fork locally**:

   ```bash
   git clone https://github.com/YOUR-USERNAME/devcontainer-template.git
   cd devcontainer-template
   ```

3. **Create a development branch**:

   ```bash
   git checkout -b feature/your-feature-name
   ```

4. **Install dependencies** and set up development tools (see README.md for language-specific instructions)
5. **Run tests locally** to ensure everything works

## Making Changes

### Code Standards

- Follow the coding standards defined in [.github/copilot-instructions.md](.github/copilot-instructions.md)
- Use meaningful variable and function names
- Write clear comments explaining "why", not "what"
- Keep functions and modules focused and single-purpose
- Maintain consistency with the existing codebase

### Commit Messages

We follow [Conventional Commits](https://www.conventionalcommits.org/). See [.github/instructions/commitMessageGeneration.instructions.md](.github/instructions/commitMessageGeneration.instructions.md) for examples.

**Format**: `<type>(<scope>): <subject>`

Examples:

- `feat: add new authentication module`
- `fix: resolve timeout in API calls`
- `docs: update installation guide`
- `test: add unit tests for user service`

### Testing

- Write tests for all new features and bug fixes
- Ensure all existing tests pass locally
- Run linting and type checks before submitting
- Aim for clear, isolated, deterministic tests

### Documentation

- Update the [README.md](README.md) if you're adding new features or changing functionality
- Add docstrings/comments to all public functions and classes
- Update relevant documentation files
- Include examples where helpful

## Submitting Changes

### Before You Submit

1. **Run local checks**:

   ```bash
   # Test (adjust command based on your project)
   # Lint
   # Type check
   ```

2. **Ensure your branch is up to date** with `main`:

   ```bash
   git fetch origin
   git rebase origin/main
   ```

3. **Push your branch**:

   ```bash
   git push origin feature/your-feature-name
   ```

### Pull Request Process

1. **Open a pull request** on GitHub
2. **Use the PR template** (automatically loaded) and fill in all sections
3. **Link related issues** (e.g., "Closes #123")
4. **Describe your changes** clearly and concisely
5. **Wait for reviews** - address feedback constructively
6. **Ensure CI passes** - all automated checks must pass

### Pull Request Checklist

- [ ] Code follows project style guidelines
- [ ] Documentation is updated
- [ ] Tests added/updated
- [ ] All tests pass locally
- [ ] No linting or type errors
- [ ] Commit messages follow Conventional Commits
- [ ] No unrelated changes included
- [ ] No hardcoded secrets or credentials

## Code Review Process

All pull requests will be reviewed for:

- **Correctness**: Does the code work as intended?
- **Quality**: Is the code well-written and maintainable?
- **Style**: Does it follow project conventions?
- **Testing**: Are there adequate tests?
- **Documentation**: Is it properly documented?
- **Security**: Are there any security concerns?

See [.github/instructions/codeReview.instructions.md](.github/instructions/codeReview.instructions.md) for detailed review guidelines.

## Types of Contributions

### Bug Reports

Found a bug? Please [open an issue](https://github.com/HYP3R00T/devcontainer-template/issues/new?template=bug_report.yml) with:

- Clear description of the issue
- Steps to reproduce
- Expected vs actual behavior
- Environment details
- Any relevant logs or screenshots

### Feature Requests

Have an idea? [Open a feature request](https://github.com/HYP3R00T/devcontainer-template/issues/new?template=feature_request.yml) with:

- Problem statement or motivation
- Proposed solution
- Alternative approaches considered
- Use cases and benefits

### Documentation Contributions

Help improve documentation by:

- Fixing typos or unclear explanations
- Adding examples or clarifications
- Improving setup instructions
- Adding troubleshooting sections

### Code Improvements

Contribute code by:

- Fixing reported bugs
- Implementing approved feature requests
- Refactoring for clarity or performance
- Adding or improving tests
- Improving error handling and logging

## Getting Help

- **Questions?** Open a discussion or reach out to maintainers
- **Stuck?** Ask in issues or discussions - we're here to help
- **Documentation unclear?** Let us know so we can improve it

## Recognition

Contributors will be recognized in:

- Commit history
- Release notes (for significant contributions)
- [CONTRIBUTORS.md](CONTRIBUTORS.md) (if maintained)

## License

By contributing to this project, you agree that your contributions will be licensed under the same license as the project. See [LICENSE](LICENSE) for details.

---

**Thank you for contributing!** Your help makes this project better for everyone. 🙏
