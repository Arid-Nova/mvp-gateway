# Contributing

Thank you for helping improve MVP Gateway.

## Development Setup

Complete the [Getting Started Guide](.doc/getting-started/getting-started.md) before making changes. Development commands and code-quality rules are documented in:

- [Gradle Workflows](.doc/development/gradle-workflows.md)
- [Code Style and Formatting](.doc/development/code-style.md)

## Ways to Contribute

- Report a reproducible bug using the bug report template.
- Propose an improvement using the feature request template.
- Improve tests or documentation.
- Submit a focused code change for an agreed issue.

Search existing issues before opening a new one. Ask a maintainer when the expected behavior or scope is unclear.

Do not report security vulnerabilities in public issues. Follow [SECURITY.md](SECURITY.md).

## Pull Requests

Pull requests should:

- Address one concern and link the related issue when one exists.
- Explain what changed and why.
- Include tests for behavior changes.
- Update documentation when setup, behavior, or usage changes.
- Pass `./gradlew check`.
- Follow the pull request template.
- Contain no generated build output, secrets, credentials, or personal configuration.

Do not document routes, security policies, or operational behavior until they are implemented.

## Review

Reviewers may request changes for correctness, scope, tests, documentation, or maintainability. Respond to feedback and keep the branch current until approval.

Review ownership is defined in [CODEOWNERS](CODEOWNERS).

## Asking for Help

Open an issue using the appropriate template. Include the goal, relevant environment details, full error output, and what you already tried. Remove secrets and personal information.
