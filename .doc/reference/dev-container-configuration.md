# Dev Container Configuration

The project Dev Container is defined in `.devcontainer/devcontainer.json`. It is the shared development environment for VS Code and IntelliJ IDEA.

## Base Image

The container uses `mcr.microsoft.com/devcontainers/java:dev-25-trixie`.

- `java` identifies the Microsoft Java Dev Container image family.
- `dev-25` supplies the Java 25 toolchain required by the build.
- `trixie` identifies the Debian base distribution.

Using a published image avoids a project-specific Dockerfile during this bootstrap stage.

## Features

### Java Feature

`ghcr.io/devcontainers/features/java:1` has Java installation disabled because the image already supplies Java 25. The Feature installs Gradle and Groovy support. Project builds still use the checked-in Gradle Wrapper as the version authority.

### Docker Outside of Docker

`ghcr.io/devcontainers/features/docker-outside-of-docker:1` connects tooling to the host Docker daemon. The `moby` option is disabled so the Feature does not install the Moby package set.

This avoids a nested Docker daemon. Docker commands in the container act on the host daemon and are privileged operations.

## VS Code Settings

| Setting | Purpose |
| --- | --- |
| `editor.detectIndentation: false` | Prevents file content from overriding project indentation |
| `editor.insertSpaces: true` | Inserts spaces when indenting |
| `editor.tabSize: 4` | Uses four columns for general indentation |
| `java.import.gradle.java.home` | Imports Gradle with the container's Java 25 installation |
| `java.compile.nullAnalysis.mode: automatic` | Enables supported annotation-based null analysis |
| `java.configuration.updateBuildConfiguration: automatic` | Refreshes Java configuration after Gradle changes |

`.editorconfig` remains the cross-editor source of truth. These VS Code defaults agree with it.

## Extensions

Extensions under `customizations.vscode` run in the container's VS Code extension host and do not configure IntelliJ IDEA. See [Visual Studio Code Extensions](vscode-extensions.md).

## Rebuild Boundary

Rebuild after changing the base image, Features, requested extensions, or container-level settings. Source, resource, and ordinary Gradle dependency changes generally need only a Gradle refresh.

## Current Limitations

- No fixed port forwarding is declared; use the IDE forwarding UI for port `8080` when necessary.
- No downstream services are provisioned.
- No production image or deployment environment is defined by the development container.