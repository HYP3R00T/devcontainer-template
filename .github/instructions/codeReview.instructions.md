# Code Review Instructions

The goal of code review is to ensure high-quality, maintainable, and secure code. Use the following checklist to review contributions.

## What to Look For

### Code Style & Structure

- Code follows project conventions and established style guides.
- All functions, methods, and class attributes are properly type-annotated (where applicable).
- Code is modular, testable, and single-purpose where applicable.
- No unnecessary complexity, redundant logic, or repeated code.
- Imports are grouped and ordered: standard library → third-party → local.

### Type Safety

- All public APIs and core logic use consistent type hints.
- Nullable/optional values are properly annotated.
- Avoid overly broad types unless unavoidable.
- Use appropriate models for structured data.

### Data Validation

- Input validation is applied to external data sources.
- Field types are precise, with appropriate constraints.
- Nested or reusable models are created for complex structures.
- Validation logic is clear and well-tested.

### Error Handling

- Use clear, actionable exception messages.
- Always raise/throw specific exception types.
- Avoid catching generic exceptions; catch only necessary ones.
- No silent failures or swallowed exceptions.

### Logging

- Errors and important events are logged appropriately.
- Logs include sufficient context for debugging.
- Appropriate severity levels are used: info, warning, error, critical.
- Avoid logging sensitive data.

### Testing

- New code is covered by tests.
- Tests are deterministic, readable, and minimal.
- External dependencies are mocked.
- Edge cases and failure paths are covered.

### Security

- All external inputs are validated.
- User-generated content and file paths are sanitized.
- No hardcoded credentials or API keys.
- Sensitive values are not logged or exposed.

## Review Suggestions

- Use clear and constructive language in comments.
- Prefer inline code suggestions when possible.
- Provide summary feedback on overall quality and risks.
- Suggest small, actionable improvements.
