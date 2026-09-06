# Prerequisites

Complete these steps on your computer. The Dev Container will provide Java and Gradle.

## General Requirements

1. Install [Git](https://git-scm.com/downloads).
2. Install and start [Docker](https://docs.docker.com/get-started/get-docker/).
3. Open a terminal on your computer and run:

```bash
git --version
docker version
```

**Expected result:** Git prints a version. Docker shows `Client` and `Server` sections.

4. Confirm Docker has at least 2 CPU cores and 4 GB of memory.
5. Confirm you can open this repository on GitHub.
6. Install one supported editor below.

## Docker Problems

| Result | What to do |
| --- | --- |
| `docker: command not found` | Install Docker, then reopen the terminal. |
| Only `Client:` appears | Start Docker and wait until it reports that the engine is running. |
| `Cannot connect to the Docker daemon` | Start Docker or configure your Linux user to access the daemon. |
| Permission denied on Linux | Follow Docker's Linux post-installation steps, then sign out and back in. |

- **Windows:** Use Docker Desktop with the WSL 2 backend.
- **macOS:** Use Docker Desktop.
- **Linux:** Use Docker Engine or Docker Desktop and configure daemon access for your user.

## Visual Studio Code

Recommended for new contributors:

1. Install [Visual Studio Code](https://code.visualstudio.com/download).
2. Open Extensions using `Ctrl+Shift+X` on Windows/Linux or `Shift+Cmd+X` on macOS. You can also select the Extensions icon in the left Activity Bar.
3. Install [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) by Microsoft.

**Expected result:** The extension page shows **Disable** or **Uninstall**.

The Java, Gradle, Spring, XML, YAML, and related workspace extensions are installed inside the container from `devcontainer.json`. Do not install each container extension manually on the host. VS Code may ask you to trust the repository before creating the container.

## IntelliJ IDEA

1. Install [IntelliJ IDEA Ultimate](https://www.jetbrains.com/idea/download/).
2. Confirm your license includes Dev Container support.
3. Start IntelliJ IDEA and complete its initial setup.

IntelliJ IDEA Community edition is not supported for this workflow.

IntelliJ runs its backend IDE inside the Dev Container and opens the project through JetBrains Client. The `customizations.vscode` section does not apply to IntelliJ, but the container image and Features do.

See [IntelliJ IDEA Workflows](../development/intellij-workflows.md) for connection steps.

## Ready to Continue

Continue when Git prints a version, Docker shows both sections, and your editor is installed.

Next, follow [Using the Dev Container](dev-container.md).

## Host-Native Development

Host-native development is possible but not recommended. It requires JDK 25 and a correct `JAVA_HOME`. Always use `./gradlew` and run `./gradlew check` before contributing.