# `com.nemis.pomodoro` (base package)

Root package of the application. It is organised by feature, with a small set of cross-cutting packages.

## Layout

| Path | Responsibility |
|---|---|
| `MainActivity.kt` | Single activity. Calls `setContent`, applies `PomodoroTheme`, hosts the navigation graph. Contains no business logic. |
| `data/` | Non-UI logic: timer engine, repositories, persistence. No Compose or Android UI imports. |
| `feature/` | One sub-package per user-facing feature (`timer`, `settings`) plus shared feature components. |
| `navigation/` | Navigation graph and route definitions connecting the features. |
| `ui/theme/` | Material 3 theme: colors, typography, shapes. |

A future `PomodoroApp.kt` (an `Application` subclass) will live directly in this package and create the app-wide dependencies (manual DI).

## Dependency direction

```
MainActivity -> navigation -> feature/* -> data
                                  |
                                  +-> ui/theme
```

- `feature` may depend on `data` and `ui`. `data` must never depend on `feature` or `ui`.
- A feature must not import another feature. Shared UI goes to `feature/components`; shared logic goes to `data`.
- `MainActivity` stays thin: if it grows, the logic belongs in a ViewModel or in `navigation`.
