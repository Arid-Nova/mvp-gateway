# Getting Started

This guide takes you from an empty computer setup to a running MVP Gateway. Follow the sections in order.

## 1. Install the Required Tools

Install:

- [Git](https://git-scm.com/downloads)
- [Docker](https://docs.docker.com/get-started/get-docker/)
- One supported editor:
  - Recommended: [Visual Studio Code](https://code.visualstudio.com/download) with [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
  - Alternative: [IntelliJ IDEA Ultimate](https://www.jetbrains.com/idea/download/)

Start Docker. Open a terminal on your computer and run:

```bash
git --version
docker version
```

**Expected result:** Git prints a version. Docker shows both `Client` and `Server` sections.

## 2. Clone the Repository

Run in a folder where you keep development projects:

```bash
git clone https://github.com/Arid-Nova/mvp-gateway.git
cd mvp-gateway
```

Open the `mvp-gateway` folder in your editor.

**Expected result:** The file explorer shows `README.md`, `build.gradle.kts`, and `src`.

## 3. Open the Dev Container

Choose the instructions for your editor.

### Visual Studio Code

1. Open the Command Palette:
   - Windows/Linux: `Ctrl+Shift+P`
   - macOS: `Shift+Cmd+P`
   - Any platform: `F1` or **View > Command Palette**
2. Type `Dev Containers: Reopen in Container`.
3. Select **Dev Containers: Reopen in Container**.
4. Trust the repository if prompted.
5. Wait for the container and Gradle import to finish.

### IntelliJ IDEA Ultimate

1. Open `.devcontainer/devcontainer.json`.
2. Select the Dev Container icon in the editor gutter.
3. Choose **Create Dev Container and Mount Sources**.
4. Select IntelliJ IDEA as the backend.
5. Wait for creation to finish, then select **Connect**.
6. Wait for Gradle import and indexing to finish.

## 4. Check the Development Environment

Open a terminal using **Terminal > New Terminal**. In VS Code, `` Ctrl+` `` works on Windows, Linux, and macOS.

Run:

```bash
pwd
java -version
./gradlew --version
```

**Expected result:**

- The path ends with `/workspaces/mvp-gateway`.
- Java reports version `25`.
- Gradle reports version `9.5.1` and JVM version `25`.

If these checks fail, confirm the editor indicates that it is connected to a Dev Container.

## 5. Verify the Project

Run:

```bash
./gradlew check
```

The first run may take several minutes while Gradle downloads dependencies.

**Expected result:** The output ends with `BUILD SUCCESSFUL`. `UP-TO-DATE` and `NO-SOURCE` are normal.

## 6. Start the Application

Run:

```bash
./gradlew bootRun
```

**Expected result:** The log contains both messages:

```text
Netty started on port 8080
Started GatewayApplication
```

Gradle may remain at `80% EXECUTING` while the server runs. This is normal. Press `Ctrl+C` in the terminal to stop it.

The bootstrap does not have gateway routes yet, so there is no downstream endpoint to test.

## 7. Next Step

Read [Contributing](../../CONTRIBUTING.md) before making changes.

For troubleshooting and additional detail, see:

- [Prerequisites](prerequisites.md)
- [Using the Dev Container](dev-container.md)
- [Running the Application](running-the-application.md)