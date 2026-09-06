# IntelliJ IDEA Workflows

IntelliJ IDEA Ultimate can use the same `devcontainer.json` as VS Code. The image and Features are shared, while IntelliJ runs its own backend IDE inside the container.

## Open the Dev Container

1. Start Docker.
2. Open the cloned repository in IntelliJ IDEA Ultimate.
3. Open `.devcontainer/devcontainer.json`.
4. Select the Dev Container gutter action.
5. Choose **Create Dev Container and Mount Sources**.
6. Select IntelliJ IDEA as the backend.
7. Monitor creation in the Services tool window.
8. Select **Connect** when creation finishes.
9. Import the Gradle project using the wrapper.

See JetBrains' [Dev Container instructions](https://www.jetbrains.com/help/idea/start-dev-container-inside-ide.html) for additional detail.

## Use the Gradle Tool Window

| Workflow | Gradle task |
| --- | --- |
| Start | `application > bootRun` |
| Test | `verification > test` |
| Verify | `verification > check` |
| Build | `build > build` |
| Clean | `build > clean` |
| Format | `other > format` |
| Check formatting | `other > checkFormat` |

Refresh the Gradle project after changing build scripts or dependencies.

## Run and Debug

Run `GatewayApplication` as a Spring Boot application for IntelliJ's debugger and run-configuration support. Run individual JUnit tests from the editor gutter or test tool window.

Use `./gradlew check` in the container terminal before contributing. It is authoritative regardless of IDE actions used during development.

## Formatting

IntelliJ honors `.editorconfig` for general whitespace. Spring Java Format is configured by Gradle and is authoritative for Java source. Run `./gradlew format` to apply it and `./gradlew checkFormat` to verify it.

Do not reconfigure IntelliJ formatting to replace the Gradle formatter. Differently formatted Java source will be rejected by `checkFormat`.

## VS Code-Specific Configuration

Entries under `customizations.vscode` do not configure IntelliJ. IntelliJ contributors still receive the same JDK, Gradle tooling, Docker access, `.editorconfig`, and repository-level Gradle checks.