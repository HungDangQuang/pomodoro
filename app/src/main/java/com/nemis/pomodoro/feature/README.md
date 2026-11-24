# `feature`

Container for user-facing features. Each sub-package is a vertical slice that owns its screen, ViewModel and UI state.

## Sub-packages

| Package | Purpose |
|---|---|
| `timer/` | Main countdown screen: current mode, remaining time, progress ring, start/pause/reset controls, completed-session counter. |
| `settings/` | Screen to change durations and related preferences. |
| `components/` | Composables reused by more than one feature (for example a themed button or section header). |

## Conventions for a feature package

Each feature follows the same file pattern (`<Name>` is the feature name):

| File | Role |
|---|---|
| `<Name>Screen.kt` | **Stateful** entry composable: obtains the ViewModel, collects state with `collectAsStateWithLifecycle()`, passes it down. |
| `<Name>Content.kt` | **Stateless** composable: receives `state` and `onEvent`. This is what `@Preview` and UI tests target. |
| `<Name>ViewModel.kt` | Holds `StateFlow<<Name>UiState>`, handles events, talks to `data`. |
| `<Name>UiState.kt` | Immutable UI state, event types (sealed interface), and small UI-only enums. |

## Rules

- A feature must not import another feature. Shared UI goes to `components/`, shared logic goes to `data/`.
- One-off effects (vibration, sound, navigation) are sent through a separate `SharedFlow`/`Channel`, not stored in `UiState`.
