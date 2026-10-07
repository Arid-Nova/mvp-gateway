# Gradle Workflows

Choose the workflow for your environment:

- **VS Code:** Prefer the Gradle view installed by the **Gradle for Java** extension.
- **Other editors, terminals, and automation:** Use the checked-in Gradle Wrapper.

Both workflows run the same Gradle tasks. The VS Code extension imports the project through the Wrapper, so it uses the repository's Gradle version.

## VS Code Gradle View

1. Connect VS Code to the Dev Container.
2. Wait for Gradle project import to finish.
3. Select the Gradle icon in the Activity Bar.
4. Expand **MVP Gateway > Tasks**.
5. Expand a task group and select the task to run it.

If the Gradle icon is missing, open **View > Open View**, search for `Gradle`, and select **Gradle Projects**.

Task output appears in the terminal. A running task appears under the Gradle view's task controls and can be stopped there. For `bootRun`, you can also focus its terminal and press `Ctrl+C`.

## Tasks and Commands

| Workflow | VS Code Gradle task | Wrapper command |
| --- | --- | --- |
| Start the application | **application > bootRun** | `./gradlew bootRun` |
| Run all tests | **verification > test** | `./gradlew test` |
| Run one test class | Use the VS Code Testing view | `./gradlew test --tests net.aridnova.mvp.gateway.GatewayApplicationTests` |
| Run all verification | **verification > check** | `./gradlew check` |
| Apply formatting | **other > format** | `./gradlew format` |
| Check formatting | **other > checkFormat** | `./gradlew checkFormat` |
| Build | **build > build** | `./gradlew build` |
| Clean | **build > clean** | `./gradlew clean` |
| Build executable JAR | **build > bootJar** | `./gradlew bootJar` |
| Build OCI image | **build > bootBuildImage** | `./gradlew bootBuildImage` |

For a clean build in VS Code, run **build > clean** and then **build > build**.

## Gradle Wrapper

Use Wrapper commands when VS Code is unavailable, when documenting a reproducible command, or when working in another editor.

Run commands from the repository root. Inside the Dev Container, Linux, and macOS, use:

```bash
./gradlew <task>
```

On Windows outside the Dev Container, use:

```powershell
.\gradlew.bat <task>
```

Replace `<task>` with a task such as `check`, `test`, or `bootRun`. A separate Gradle installation is not required.

List all available tasks with:

```bash
./gradlew tasks --all
```

## Task Results

Gradle skips work when inputs and outputs have not changed. A message such as `8 actionable tasks: 8 up-to-date` is successful.

The suggestion to enable configuration cache is informational. Configuration cache is not enabled because the current Spring Java Format tasks are incompatible with it.

## Refreshing Dependencies

First refresh the project from the Gradle view. Use the command below only when diagnosing stale dependency metadata:

```bash
./gradlew build --refresh-dependencies
```

This should not be the default because it bypasses useful caching.

## Reports

Test and Checkstyle reports are written under `build/reports`. The generated `build` directory must not be committed.

See [Code Style and Formatting](code-style.md) for checks attached to the Gradle lifecycle.