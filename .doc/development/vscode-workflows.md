# Visual Studio Code Workflows

The Dev Container installs the Java, Spring, Gradle, testing, XML, and YAML extensions used by the project. Wait for Java and Gradle import to finish before relying on task or dependency views.

## Open the Project

Follow [Using the Dev Container](../getting-started/dev-container.md). The remote indicator should show that VS Code is connected to the container.

## Use the Gradle View

The Gradle view is the preferred way to run project tasks in VS Code.

1. Select the Gradle icon in the Activity Bar.
2. Expand **MVP Gateway > Tasks**.
3. Expand a task group.
4. Select a task to run it.

Tasks run in VS Code terminals. Long-running tasks such as `bootRun` remain active until stopped. Use the Gradle task controls or press `Ctrl+C` in its terminal.

See [Gradle Workflows](gradle-workflows.md) for the task map and equivalent Wrapper commands.

## Run and Debug Java

Open `GatewayApplication.java` and use the **Run** or **Debug** action above `main`. The Java debugger supports breakpoints, stepping, variable inspection, and supported hot code replacement.

Use **application > bootRun** in the Gradle view for normal startup. Use the editor's **Debug** action when you need breakpoints.

## Run Tests

Use the Testing view or the run/debug action beside a test class or method. The current bootstrap test is `GatewayApplicationTests.contextLoads`.

The Testing view is useful for focused tests. Before opening a pull request, run **verification > check** in the Gradle view because it also runs formatting and Checkstyle checks.

## Format Java

Spring Java Format, invoked through Gradle, is authoritative for Java source:

1. Open the Gradle view.
2. Expand **MVP Gateway > Tasks > other**.
3. Run **format** to update all main and test Java source.
4. Review the resulting changes.
5. Run **checkFormat** for a formatting-only verification, or run
   **verification > check** for complete project verification.

The Dev Container configures VS Code to use spaces and four-space indentation, while
`.editorconfig` supplies the repository's general whitespace rules. These editor settings
prevent common mistakes but do not replace Spring Java Format.

Do not rely on **Format Document**, format-on-save, or another Java formatter as the final
formatting step. If VS Code produces output that differs from Gradle, keep the output from the
Gradle **format** task.

## Refresh Project Configuration

Gradle build changes are imported automatically. If the classpath or tasks are stale:

1. Refresh the project in the Gradle view.
2. Run **Java: Reload Projects**.
3. If necessary, run **Java: Clean Java Language Server Workspace** and reload.

## Spring Tooling

Spring Boot Tools provides completion and validation for `application.properties`, navigation for Spring beans and request mappings, and integration with running applications. Spring Boot Dashboard can start, stop, and inspect discovered applications.

See [Visual Studio Code Extensions](../reference/vscode-extensions.md) for the complete inventory.