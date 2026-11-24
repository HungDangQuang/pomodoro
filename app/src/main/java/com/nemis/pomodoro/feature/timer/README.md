# `feature/timer`

The main screen of the app: a Pomodoro countdown.

## Should contain

| File | Description |
|---|---|
| `TimerScreen.kt` | Stateful composable. Gets `TimerViewModel`, collects `TimerUiState`, forwards events. |
| `TimerContent.kt` | Stateless composable that draws the screen from `TimerUiState` and calls `onEvent(TimerEvent)`. Has `@Preview`s for each mode and for running/paused. |
| `TimerViewModel.kt` | Combines `TimerEngine` and settings into one `StateFlow<TimerUiState>`. Handles start, pause, reset, skip, and automatic mode switching. |
| `TimerUiState.kt` | `TimerUiState` (`remainingMillis`, `totalMillis`, `mode`, `isRunning`, `completedSessions`, derived `progress`), `TimerMode` (`Focus`, `ShortBreak`, `LongBreak`), and `TimerEvent` (`Start`, `Pause`, `Reset`, `Skip`). |
| `components/` (optional) | Composables used only by this screen: circular progress drawn with `Canvas`, mode chip, control buttons. Move them to `feature/components` only when a second feature needs them. |

## Behaviour to implement

- Focus, then short break; after N focus sessions, a long break; then the cycle restarts.
- Mode colors come from the theme, not hard-coded in the screen.
- The ViewModel owns the timer (not a `LaunchedEffect`), so it survives recomposition and rotation.

## Should not contain

- Time arithmetic or mode-transition rules (they live in `data`).
- Direct DataStore or file access.
