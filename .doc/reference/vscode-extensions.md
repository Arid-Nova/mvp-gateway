# Visual Studio Code Extensions

The Dev Container requests Java and Spring development extensions under `customizations.vscode.extensions`. They run inside the container and can access its JDK, Gradle project, and source tree.

## Extension Inventory

| Extension ID | Role and use |
| --- | --- |
| `vscjava.vscode-java-pack` | Bundles Java language support, debugging, testing, Maven, Gradle, and project management extensions |
| `vmware.vscode-boot-dev-pack` | Bundles Spring Boot Tools, Spring Initializr, Spring Boot Dashboard, and a walkthrough |
| `fwcd.kotlin` | Kotlin language tooling; Gradle remains authoritative for Kotlin DSL evaluation |
| `leksandrhavrysh.intellij-formatter` | Requested IntelliJ-style formatter that may not be available on every platform; it is not authoritative for Java |
| `redhat.vscode-xml` | Validate, complete, navigate, and format the Checkstyle XML configuration |
| `redhat.vscode-yaml` | Validate and complete YAML, including future workflow files |

Bundle members are not listed separately in `devcontainer.json`. The Java Extension Pack supplies `redhat.java`, `vscjava.vscode-java-debug`, `vscjava.vscode-java-test`, `vscjava.vscode-maven`, `vscjava.vscode-gradle`, and `vscjava.vscode-java-dependency`. The Spring Boot Extension Pack supplies `vmware.vscode-spring-boot`, `vscjava.vscode-spring-initializr`, and `vscjava.vscode-spring-boot-dashboard`.

The Java pack includes Maven tooling, but this repository uses Gradle. Use the Gradle Wrapper and Gradle view for project tasks.

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