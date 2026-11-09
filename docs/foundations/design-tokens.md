# Design tokens

`@paraxe/design` has a layered CSS contract. `tokens.css` provides structural tokens (spacing, layout, typography, radius, shadow, motion, and component structure). Theme files provide colour tokens. Presets tune the same token system.

```ts
import "@paraxe/design/tokens.css";
import "@paraxe/design/themes/dark.css";
import "@paraxe/design/presets/default.css";
import "@paraxe/design/components.css";
```

At runtime, `token(name)` returns a CSS `var(...)` reference for the exported `TokenName` or `ColorTokenName` types. Use tokens such as `var(--space-4)` and `var(--text-primary)` instead of hard-coded equivalents when extending UI.

The design package source comments still identify the package as “Loba”; this is a branding inconsistency in the implementation and should be corrected before treating those comments as public Paraxe copy.
