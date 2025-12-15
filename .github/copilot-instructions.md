# Project Coding Standards

## Naming Conventions

Follow the project's established naming conventions:

- Use consistent naming patterns for variables, functions, methods, and types.
- Use appropriate case conventions for identifiers (e.g., camelCase, snake_case, PascalCase).
- Use meaningful, descriptive names that convey intent.
- Prefix unused or private variables/members with an underscore where appropriate.

## Type Safety

Use static typing where the language supports or recommends it:

- Provide type hints/annotations for all public APIs.
- Use nullable/optional types appropriately (e.g., `T | None`, `Optional<T>`, `?T`).
- Avoid overly broad types like `Any`, `unknown`, or `Object` unless unavoidable.
- Use domain-specific types and validation models for structured data.
- Define clear contracts between functions and modules.

## Data Modeling and Validation

- Use language-appropriate validation libraries (e.g., Pydantic for Python, Zod for TypeScript, Hibernate/Jackson for Java).
- Define strict, well-documented types for model fields.
- Validate all external inputs (API requests, file uploads, user input).
- Use reusable, composable models rather than inline structures.
- Document field constraints and requirements.

## Error Handling

- Raise or throw exceptions with specific, actionable messages.
- Use specific exception types rather than generic ones.
- Avoid silent failures or swallowed exceptions.
- Log errors with appropriate severity levels and context.
- Handle external failures (I/O, network, database) gracefully with proper recovery strategies.

## Formatting and Style

- Follow the project's established style guides and conventions.
- Use standard formatting tools (where available for your language).
- Organize imports logically: standard library → third-party → local.
- Keep code modular, readable, and single-purpose.
- Maintain consistent indentation and whitespace.

## Documentation

- Write clear comments explaining the "why", not the "what".
- Use appropriate documentation standards for your project.
- Document public APIs, parameters, return types, and exceptions.
- Keep functions and modules small and focused.
- Maintain a README with setup and usage instructions.

## Test and CI Guidelines

- Write tests for new features and bug fixes using standard testing frameworks.
- Aim for clear, isolated, and deterministic tests.
- Mock external dependencies appropriately.
- Run linting, formatting, and type checks in CI.
- All pull requests must pass tests and code quality checks before merging.
- Keep test code as maintainable as production code.

## General Principles

- **Code Quality**: Prioritize readability and maintainability over cleverness.
- **DRY (Don't Repeat Yourself)**: Avoid duplication; extract common logic into reusable utilities.
- **SOLID Principles**: Write modular, loosely coupled code that's easy to test and extend.
- **Security**: Validate inputs, avoid hardcoded secrets, sanitize user data, handle authentication securely.
- **Performance**: Write efficient code, but prioritize clarity unless performance is critical.
