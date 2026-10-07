# MVP Gateway

MVP Gateway is the API gateway for the MVP platform. It will provide one entry point for client requests and apply shared routing and security rules before forwarding requests to platform services.

The project is currently in its **bootstrap milestone**. The Spring Boot application starts and the Spring Cloud Gateway dependencies load, but routes and application-specific security rules are not implemented yet.

## Current Scope

| Available now | Planned for later work |
| --- | --- |
| Runnable Spring Boot application | Routes to downstream services |
| Reactive Spring Cloud Gateway foundation | Authentication and authorization policy |
| Actuator and security dependencies | Rate limiting, retries, and CORS policy |
| Gradle build, tests, formatting, and Checkstyle | Production deployment and operations |
| Reproducible Dev Container | Additional gateway behavior |

## Technology

- Java 25
- Spring Boot 4.1
- Spring Cloud Gateway with WebFlux
- Gradle Wrapper
- Spring Java Format and Checkstyle

## Getting Started

New contributors should follow the self-contained [Getting Started Guide](.doc/getting-started/getting-started.md). It covers installation, cloning, Dev Container setup in VS Code and IntelliJ IDEA, project validation, and application startup.

No previous Java, Gradle, Spring, Docker, or Dev Container experience is required.

## Important to Know

- Use the Dev Container for the supported development environment.
- In VS Code, prefer the Gradle view. Outside VS Code, use the checked-in Gradle Wrapper.
- Run the Gradle `check` task before opening a pull request.
- The application listens on port `8080` when running.
- `bootRun` remains active while the server runs; a percentage such as `80% EXECUTING` is normal.
- No gateway routes are available during the bootstrap milestone.
- GitHub Actions workflows have not been implemented yet.

## Development Workflow

VS Code contributors should run tasks from the **Gradle for Java** extension. Contributors using another editor or a terminal should use `./gradlew`. Both methods use the checked-in Gradle version.

See [Gradle Workflows](.doc/development/gradle-workflows.md) for task locations, equivalent commands, and expected results.

## Documentation

### Contributor Guides

- [Getting Started Guide](.doc/getting-started/getting-started.md)
- [Contributing Guide](CONTRIBUTING.md)

### Development Reference

- [Gradle Workflows](.doc/development/gradle-workflows.md)
- [Visual Studio Code Workflows](.doc/development/vscode-workflows.md)
- [IntelliJ IDEA Workflows](.doc/development/intellij-workflows.md)
- [Code Style and Formatting](.doc/development/code-style.md)
- [Dev Container Configuration](.doc/reference/dev-container-configuration.md)
- [Visual Studio Code Extensions](.doc/reference/vscode-extensions.md)

The Getting Started Guide links to detailed prerequisite, Dev Container, and application startup help when needed.

## Ownership

Review ownership is defined in [CODEOWNERS](CODEOWNERS): `@Arid-Nova/developers` owns project files by default, while `@Arid-Nova/admins` owns governance, security, licensing, and `.github/` files.

The repository includes issue and pull request templates. GitHub Actions workflows have not been implemented yet; the workflows directory currently contains only a placeholder.

## Security

Do not report vulnerabilities in public issues. Follow the private reporting process in [SECURITY.md](SECURITY.md).

## License

See [LICENSE](LICENSE).
