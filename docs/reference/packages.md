# Packages and exports

| Package | Public purpose |
| --- | --- |
| `@paraxe/core` | Shared TypeScript contracts and types |
| `@paraxe/design` | CSS tokens, themes, presets, component styles, token helpers |
| `@paraxe/vue` | Vue components and a resolver subpath |
| `@paraxe/react` | React components |

The current Vue and React barrels both export Avatar, Icon, Divider, Menu, and Video. Export presence does not guarantee identical behaviour in older package versions: for example, React Avatar gains the full image/size/shape/status API in React 0.4.0. Read [release status](release-status.md), the component's guide, and installed declarations for the version in use. Core provides shared contracts and helpers; rendering and slots/callbacks remain framework-specific.

Both framework barrels also export Calendar, Fieldset, InputGroup, Spinner, Stepper, Stat, and Sparkline. The new parity work and Checkbox identity/description/invalid props ship in Vue 1.5.0/React 0.4.0 with core 1.6.0/design 1.10.0. See [Stat](../components/stat.md) and [Checkbox](../components/checkbox.md).
