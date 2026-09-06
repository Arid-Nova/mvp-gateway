# Copilot instructions

## Repository status

- This repository is the initial Spring Boot and Spring Cloud Gateway bootstrap.
- The application starts, but gateway routes and application-specific security
  rules are intentionally deferred to later work.
- The project uses Java 25, Gradle, Spring Java Format, and Checkstyle.
- Preserve the existing Java-oriented ignore rules in `.gitignore` unless the project technology changes.

## Working in this repository

- Read the current `README.md` and inspect the repository before introducing project structure or tooling.
- Use `./gradlew bootRun` to start the application.
- Use `./gradlew build` to build the project and `./gradlew check` for complete verification.
- Use `./gradlew test` to run all tests.
- Use `./gradlew test --tests net.aridnova.mvp.gateway.GatewayApplicationTests` to run the bootstrap test class.
- Use `./gradlew format` to apply Java formatting and `./gradlew checkFormat` to check it.
- Prefer the Dev Container workflow documented under `.doc/`.
- Keep this file focused on repository-specific guidance; avoid adding generic programming advice.
