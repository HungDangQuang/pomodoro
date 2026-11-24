# `data`

Non-UI logic of the app: how time is counted and how preferences are stored.

## Should contain

| Item | Description |
|---|---|
| `TimerEngine` | Pure Kotlin countdown. Stores an absolute `endTimeMillis` and computes `remaining = endTime - now` on every tick, so it does not drift. Exposes a `Flow` of remaining time. Takes a clock/time source as a parameter so tests can fake time. |
| `nextMode(...)` | Pure function deciding the next mode (focus, short break, long break) from the current mode, completed sessions and settings. |
| `SettingsRepository` | Reads and writes user preferences (focus, short break and long break durations, sessions before a long break) through DataStore. Exposes `Flow<Settings>`. |
| Data models | Plain `data class` / `enum` types used by the repositories, such as `Settings` and `TimerMode`. |

## Should not contain

- Composables, `ViewModel`s, or anything from `androidx.compose.*`.
- Direct references to `Context` in logic that can be tested on the JVM. Pass dependencies in through constructors.
- Screen-specific UI state (that belongs to the feature's `*UiState`).

## Testing

Everything here should be unit-testable on the JVM (`src/test`) using `kotlinx-coroutines-test` and, for Flows, Turbine.

## Future additions

A `SessionRepository` backed by Room can be added here for history and statistics without changing the UI layer's structure.
