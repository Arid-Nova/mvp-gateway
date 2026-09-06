# Using the Dev Container

Complete [Prerequisites](prerequisites.md) first. Run validation commands in an editor terminal after connecting to the container.

## Visual Studio Code

1. Start Docker.
2. Open the `mvp-gateway` folder in VS Code.
3. Open the Command Palette.

| Platform | Shortcut |
| --- | --- |
| Windows/Linux | `Ctrl+Shift+P` or `F1` |
| macOS | `Shift+Cmd+P` or `F1` |

You can also select **View > Command Palette** from the menu.

4. Type `Dev Containers: Reopen in Container` and select it.
5. Trust the repository if prompted.
6. Wait for the container and Gradle import to finish.
7. Confirm the lower-left corner indicates a Dev Container.
8. Open a terminal using **Terminal > New Terminal**. The shortcut is `` Ctrl+` `` on Windows, Linux, and macOS.
9. Run:

```bash
pwd
java -version
./gradlew --version
```

**Expected result:**

- `pwd` ends with `/workspaces/mvp-gateway`.
- Java reports version `25`.
- Gradle reports version `9.5.1` and JVM version `25`.

Terminals opened after connection run inside the container. Source changes remain visible in the host working tree.

## IntelliJ IDEA

1. Start Docker.
2. Open the `mvp-gateway` folder in IntelliJ IDEA Ultimate.
3. Open `.devcontainer/devcontainer.json`.
4. Select the Dev Container gutter icon.
5. Choose **Create Dev Container and Mount Sources**.
6. Select IntelliJ IDEA as the backend.
7. Wait for creation and select **Connect**.
8. Wait for Gradle import and indexing.
9. Open the terminal and run the validation commands above.

JetBrains documents this workflow in [Start Dev Container inside IDE](https://www.jetbrains.com/help/idea/start-dev-container-inside-ide.html).

## Verify the Project

Run:

```bash
./gradlew check
```

**Expected result:** The output ends with `BUILD SUCCESSFUL`. `UP-TO-DATE` and `NO-SOURCE` are normal.

## Rebuild the Container

Rebuild after changes to `.devcontainer/devcontainer.json`, its image, Features, requested extensions, or container settings.

### Visual Studio Code

1. Open the Command Palette with `Ctrl+Shift+P` on Windows/Linux, `Shift+Cmd+P` on macOS, or `F1` on any platform.
2. Type `Dev Containers: Rebuild Container`.
3. Select **Dev Containers: Rebuild Container**.
4. Wait for VS Code to reconnect and Gradle import to finish.

You can also select the remote indicator in the lower-left corner and choose **Rebuild Container**.

### IntelliJ IDEA

1. Open `.devcontainer/devcontainer.json`.
2. Select the Dev Container gutter icon.
3. Choose **Create Dev Container and Mount Sources**.
4. Reconnect when creation finishes.

Only rebuild after container configuration changes. Source changes need no rebuild.

## Docker Access

The container uses the host Docker daemon instead of running a nested daemon. Verify access from a container terminal with `docker version`.

Access to the host daemon is privileged access. Only open and run trusted repository content in the container.

## Ports

The application listens on port `8080` inside the container. The current configuration does not declare a fixed forwarded port. Use the IDE's port-forwarding interface if `localhost:8080` is not available automatically.

## Troubleshooting

| Symptom | Check | Action |
| --- | --- | --- |
| **Reopen in Container** is missing in VS Code | Open Extensions and find Dev Containers | Install or enable the Microsoft Dev Containers extension. |
| Container creation fails immediately | Run the Docker verification command from [Prerequisites](prerequisites.md) | Start Docker and confirm Client and Server sections appear. |
| Workspace path does not start with `/workspaces/` | Check the editor's remote indicator | Reopen or reconnect to the Dev Container. |
| Java is not version 25 | Run the validation commands above | Rebuild the container; the expected Java home is `/usr/lib/jvm/msopenjdk-current`. |
| Gradle tasks do not appear | Check whether project import is still active | Wait, then refresh the Gradle project. |
| Build behavior appears stale | Stop Gradle using the command below | Run the project verification again. |
| A Feature or extension change is missing | Check whether `devcontainer.json` changed | Rebuild the container instead of only reloading the editor. |

```bash
./gradlew --stop
./gradlew check
```

For help, provide your operating system, editor, failed step, and full error. Remove secrets.

See [Dev Container Configuration](../reference/dev-container-configuration.md) for the rationale behind each setting.