# `feature/components`

Reusable Composables shared by two or more features.

## Should contain

- Small, stateless, generic building blocks: buttons, cards, section headers, dialogs, icon wrappers.
- Each component takes all its data and callbacks as parameters, exposes a `modifier: Modifier = Modifier` parameter, and ships with a `@Preview`.

## Should not contain

- Anything that depends on a specific ViewModel or feature state.
- A composable used by only one feature. Keep it in that feature's own `components/` folder until a second user appears.
- Theme definitions (they belong in `ui/theme`).
