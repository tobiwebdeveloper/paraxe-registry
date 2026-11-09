# Packages and exports

| Package | Public purpose |
| --- | --- |
| `@paraxe/core` | Shared TypeScript contracts and types |
| `@paraxe/design` | CSS tokens, themes, presets, component styles, token helpers |
| `@paraxe/vue` | Vue components and a resolver subpath |
| `@paraxe/react` | React components |

The Vue barrel does not export its source `Avatar.vue`, `Icon.vue`, or `Divider.vue`; they are intentionally excluded from the Vue public index. The React barrel exports `Avatar`, `Icon`, `Divider`, `Menu`, and `Video`. Core does not export contracts for every framework-specific component. These differences are documented rather than normalised by this site.
