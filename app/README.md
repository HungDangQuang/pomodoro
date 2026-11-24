# `app` module

The only Gradle module of the project. It builds the installable Android application.

## Contents

| Path | Purpose |
|---|---|
| `build.gradle.kts` | Module build script: SDK levels, Compose setup, dependencies (resolved through `gradle/libs.versions.toml`) |
| `src/main/` | Production code and resources |
| `src/test/` | JVM unit tests |
| `src/androidTest/` | Instrumented and Compose UI tests |

## Rules

- Add new dependencies to the version catalog (`gradle/libs.versions.toml`) first, then reference them with `libs.*` here. Do not hard-code versions in this file.
- Keep the module single until there is a concrete reason to split it (build time, reuse). Package boundaries inside `src/main/java` already separate concerns.
- Do not commit the `build/` directory.
