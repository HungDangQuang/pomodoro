# `navigation`

Defines how the user moves between screens.

## Should contain

| File | Description |
|---|---|
| `AppNavGraph.kt` | The `NavHost` and its destinations (`Timer` and `Settings`). Called from `MainActivity` inside the theme. |
| `Routes.kt` (or `Destinations.kt`) | Route definitions, preferably type-safe (serializable route objects) rather than raw strings. |

## Rules

- This package wires screens together; it contains no screen UI and no business logic.
- Screens receive navigation as plain lambdas (for example `onOpenSettings: () -> Unit`) instead of a `NavController`, so they stay previewable and testable.
- Requires the Navigation Compose dependency, to be added to `gradle/libs.versions.toml` when this package is first implemented.
