# Code Style and Formatting

Repository-level files and Gradle tasks enforce code quality independently of the contributor's IDE.

## Why Spring Java Format Is Required

The project uses Spring Java Format because it provides one deterministic Java style that
matches the Spring ecosystem used by this application. A shared formatter:

- prevents VS Code, IntelliJ IDEA, and command-line contributors from producing competing
  styles;
- keeps pull request diffs focused on behavior instead of whitespace;
- makes formatting reproducible locally and in automated verification; and
- removes subjective formatting decisions from code review.

All contributors must use the repository's Gradle formatting tasks for Java source. IDE
formatters may help while editing, but they must not replace Spring Java Format or override its
output. Formatting is part of the build contract: a change that fails `checkFormat` or `check`
is not ready to merge.

## Authoritative Checks

```bash
./gradlew check
```

The `check` lifecycle includes Spring Java Format verification, Checkstyle analysis, Java compilation, and JUnit tests for main and test source where applicable.

Apply Java formatting with `./gradlew format`. Check it without changing files with `./gradlew checkFormat`.

Spring Java Format controls Java wrapping and whitespace. It is not a general formatter for Gradle, XML, JSON, YAML, or Markdown.

## Required Formatting Style

The repository uses:

- spaces rather than tabs;
- four-space indentation for Java and other files unless overridden;
- two-space indentation for JSON and YAML;
- LF line endings;
- a final newline; and
- no trailing whitespace.

Spring Java Format also owns Java line wrapping and whitespace. Spring Checkstyle owns
additional Java conventions such as import ordering and structural rules. Contributors should
not manually restyle formatter output.

`.springjavaformatconfig` changes Spring Java Format's default indentation from tabs to spaces.
`.editorconfig` defines the repository-wide whitespace rules and the JSON and YAML override.

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

## Contributor Workflow

Before committing Java changes:

1. Run `./gradlew format`.
2. Review the formatter's changes with the rest of your work.
3. Run `./gradlew check`.

The final command verifies formatting, Checkstyle, compilation, and tests. Run
`./gradlew checkFormat` when you only need a non-modifying formatting check.