# `feature/settings`

Screen where the user adjusts timer preferences.

## Should contain

| File | Description |
|---|---|
| `SettingsScreen.kt` | Stateful composable. Gets `SettingsViewModel`, collects `SettingsUiState`. |
| `SettingsContent.kt` | Stateless composable with the form controls (sliders or steppers for focus, short break and long break minutes, and sessions before a long break). Has `@Preview`s. |
| `SettingsViewModel.kt` | Reads settings from `SettingsRepository`, validates input, writes changes back. |
| `SettingsUiState.kt` | Immutable state for the form and the events the screen can emit. |

## Rules

- Persistence goes through `SettingsRepository` in `data/`; this package never touches DataStore directly.
- Validate values (minimum and maximum minutes) in the ViewModel, not in the composable.
- Changing a setting while a timer is running must not corrupt the running session: define clearly whether it applies immediately or from the next session, and document it here.
