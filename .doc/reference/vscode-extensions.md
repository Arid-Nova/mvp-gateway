# Visual Studio Code Extensions

The Dev Container requests Java and Spring development extensions under `customizations.vscode.extensions`. They run inside the container and can access its JDK, Gradle project, and source tree.

## Extension Inventory

| Extension ID | Role and use |
| --- | --- |
| `redhat.java` | Java completion, diagnostics, navigation, refactoring, import organization, and Gradle import |
| `vscjava.vscode-java-debug` | Debug `GatewayApplication.main` with breakpoints, stepping, and variable inspection |
| `vscjava.vscode-java-test` | Run or debug JUnit tests from editor actions or the Testing view |
| `vscjava.vscode-java-dependency` | Inspect project structure and dependencies; edit managed dependencies in Gradle rather than adding JARs manually |
| `vscjava.vscode-gradle` | Browse dependencies and run, pin, debug, or stop Gradle tasks |
| `vmware.vscode-spring-boot` | Spring-aware navigation and completion for Java and `application.properties` |
| `vmware.vscode-boot-dev-pack` | Bundles Spring Boot Tools, Spring Initializr, Spring Boot Dashboard, and a walkthrough |
| `vscjava.vscode-spring-initializr` | Generate separate Spring projects; it is not the dependency editor for this Gradle project |
| `fwcd.kotlin` | Kotlin language tooling; Gradle remains authoritative for Kotlin DSL evaluation |
| `leksandrhavrysh.intellij-formatter` | Requested IntelliJ-style formatter that may not be available on every platform; it is not authoritative for Java |
| `redhat.vscode-xml` | Validate, complete, navigate, and format the Checkstyle XML configuration |
| `redhat.vscode-yaml` | Validate and complete YAML, including future workflow files |

The Spring Boot Extension Pack overlaps with explicitly listed Spring Boot Tools and Spring Initializr. VS Code installs one copy of each; the pack also supplies Spring Boot Dashboard.

## Authoritative Build and Formatting

IDE tooling is a development aid. The Gradle Wrapper is authoritative:

```bash
./gradlew check
```

Do not rely on the IntelliJ-style formatter extension for Java. Use `./gradlew format` and `./gradlew checkFormat`.

## Main Views

- Use the Gradle view to browse projects, tasks, and dependencies.
- Use the Testing view for JUnit execution and results.
- Use Java Projects to inspect source sets and dependencies.
- Use Spring Boot Dashboard to start or stop discovered applications.
- Use **Java: Reload Projects** after a classpath change that did not refresh automatically.

If the Gradle view is empty, wait for import, refresh the view, and inspect the **Gradle for Java** output channel.

## Changing the Extension Set

Change shared extensions in `.devcontainer/devcontainer.json`, then rebuild. Personal extensions that do not affect the shared workflow should remain user-level choices.