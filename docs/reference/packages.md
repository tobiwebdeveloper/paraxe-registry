# Packages and exports

| Package | Public purpose |
| --- | --- |
| `@paraxe/core` | Shared TypeScript contracts and types |
| `@paraxe/design` | CSS tokens, themes, presets, component styles, token helpers |
| `@paraxe/vue` | Vue components and a resolver subpath |
| `@paraxe/react` | React components |

The current Vue and React barrels both export Avatar, Icon, Divider, Menu, and Video. Export presence does not guarantee identical behaviour in older package versions: for example, React Avatar gains the full image/size/shape/status API in development after 0.2.0. Read [release status](release-status.md), the component's guide, and installed declarations for the version in use. Core provides shared contracts and helpers; rendering and slots/callbacks remain framework-specific.
