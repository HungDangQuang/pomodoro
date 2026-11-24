# `ui`

App-wide UI infrastructure that is not tied to a single feature.

## Sub-packages

| Package | Purpose |
|---|---|
| `theme/` | Material 3 theme: `Color.kt`, `Type.kt`, `Theme.kt` (`PomodoroTheme`). |

## Possible future additions

- `ui/util/`: small Compose helpers (for example a time formatter such as `mm:ss`, or modifier extensions).

## Rules

- No feature-specific screens or state here.
- Visual constants (colors, typography, spacing) are defined once here and consumed through `MaterialTheme`.
