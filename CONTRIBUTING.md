# Contributing

Thanks for helping improve this Java and Spring Boot microservices learning project.

## Before you start

- Read the [README](README.md) and [roadmap](docs/ROADMAP.md).
- Keep each change focused on one feature, fix, or documentation improvement.
- Check existing issues and pull requests before starting work.
- For a large design change, open an issue or discussion first.

## Suggested workflow

1. Create a branch from the latest `main`: `feat/short-description`, `fix/short-description`, or `docs/short-description`.
2. Make a small, understandable change.
3. Add or update tests for behavior changes.
4. Update relevant documentation and examples.
5. Run the checks available for the module.
6. Commit with a descriptive message, such as `feat: add product validation`.
7. Open a pull request explaining the change and how it was verified.

## Code guidelines

- Use clear names and keep methods focused.
- Prefer constructor injection in Spring components.
- Keep controllers thin; put business rules in a service/domain layer.
- Validate external input and return predictable error responses.
- Never log passwords, tokens, personal data, or secrets.
- Configure explicit timeouts for network calls.
- Avoid automatic retries without considering idempotency and retryable errors.
- Test success cases, invalid input, and important failure paths.

## Pull request checklist

- [ ] The change has a clear purpose and scope.
- [ ] Tests were added or updated where appropriate.
- [ ] Existing tests and build checks pass, or failures are explained.
- [ ] Documentation and examples are current.
- [ ] No credentials, local environment files, or generated build output are committed.
- [ ] New configuration has a safe example and is documented.

## Reporting issues

Include expected behavior, actual behavior, reproduction steps, relevant logs with secrets removed, and environment details (Java, Maven, operating system, and module).
