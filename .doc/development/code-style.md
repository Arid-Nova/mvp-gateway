# Code Style and Formatting

Repository-level files and Gradle tasks enforce code quality independently of the contributor's IDE.

## Authoritative Checks

```bash
./gradlew check
```

The `check` lifecycle includes Spring Java Format verification, Checkstyle analysis, Java compilation, and JUnit tests for main and test source where applicable.

Apply Java formatting with `./gradlew format`. Check it without changing files with `./gradlew checkFormat`.

Spring Java Format controls Java wrapping and whitespace. It is not a general formatter for Gradle, XML, JSON, YAML, or Markdown.

## Space Indentation

The project uses spaces, not tabs.

`.springjavaformatconfig` changes Spring Java Format's default indentation from tabs to spaces. `.editorconfig` applies spaces, LF line endings, final newlines, and trailing-whitespace cleanup. JSON and YAML use two spaces; other files use four spaces.

The Dev Container configures VS Code to insert spaces and disables indentation detection so existing tabs cannot silently change editor behavior.

## Spring Checkstyle Rules

The Gradle build applies Checkstyle `9.3` and checks supplied by Spring Java Format `0.0.48`. These enforce Spring-oriented conventions beyond whitespace, including import ordering and structural checks.

The project configuration in `config/checkstyle/checkstyle.xml` retains Spring's checks except for:

| Excluded check | Reason |
| --- | --- |
| `SpringHeaderCheck` | This repository must not copy the Spring project's copyright header; licensing is defined by this repository's `LICENSE`. |
| `JavadocPackageCheck` | Package-level `package-info.java` documentation is not required for this bootstrap. |

These exclusions do not disable formatting, import-order checks, tests, or the remaining Spring checks.

## IDE Responsibilities

Editor formatting is a convenience. Gradle is authoritative in VS Code, IntelliJ IDEA, and host-native environments. When an IDE and Gradle disagree, run `./gradlew format`, review the changes, and run `./gradlew check`.

Do not weaken checks solely to accommodate an IDE default.