# Running the Application

The current application is a Spring Cloud Gateway bootstrap. It proves that the Spring application and gateway dependencies load, but it does not define routes or application-specific security rules.

Run all commands in the Dev Container from `/workspaces/mvp-gateway`.

## Verify the Project First

Open a new editor terminal and run:

```bash
./gradlew check
```

This runs formatting checks, Checkstyle, compilation, and tests.

**Expected result:** The output ends with `BUILD SUCCESSFUL`. `UP-TO-DATE` is also successful.

## Start with Gradle

In the same terminal, run:

```bash
./gradlew bootRun
```

Wait for both startup messages:

```text
Netty started on port 8080 (http)
Started GatewayApplication
```

**Expected result:** Both messages appear. `80% EXECUTING` is normal while the server runs.

Press `Ctrl+C` to stop the application.

**Expected result:** The command prompt returns.

## Start from an IDE

- In VS Code, run `application > bootRun` from the Gradle view or use the Run action above `GatewayApplication.main`.
- In IntelliJ IDEA, run `bootRun` from the Gradle tool window or run `GatewayApplication` as a Spring Boot application.

The Gradle `bootRun` task is the reference workflow because it behaves consistently in terminals, IDEs, and automation.

## Development Restarts

Spring Boot DevTools is a development-only dependency. When compiled classpath files change, DevTools may gracefully stop Netty and restart the application. Logs such as `Restarting due to ... class path changes` are expected during development.

## Current HTTP Behavior

The server listens on port `8080`, and Actuator is included. No gateway routes are configured, so there is no downstream service to proxy. Spring Security dependencies are present, but this bootstrap does not define the gateway's eventual authentication or authorization policy.

Later changes will add and document routing and security behavior. Do not infer those future contracts from this bootstrap.

## Startup Troubleshooting

| Symptom | Likely cause | Action |
| --- | --- | --- |
| `./gradlew: Permission denied` | Wrapper execute permission is missing | Run the permission command below, then retry. |
| `JAVA_HOME` or Java version error | Command is running outside the Dev Container | Reconnect to the container and run the Java version command below. |
| `Port 8080 was already in use` | Another application is using the port | Stop the other application or an earlier `bootRun`, then retry. |
| Gradle remains at `80% EXECUTING` after startup messages | The server is running normally | Leave it running or stop it with `Ctrl+C`. |
| Startup ends with `BUILD FAILED` | Compilation, configuration, or runtime failure | Read the first error, retain the complete output, and ask for help if the corrective action is unclear. |

```bash
chmod +x gradlew
java -version
```