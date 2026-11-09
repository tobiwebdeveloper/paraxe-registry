# Project setup

The [installation guide](../guides/install-and-theme.md) covers generating a project-owned preset and theme with explicit output paths. Import CSS once in your application entry, in this order:

```ts
import "@paraxe/design/style.css";
import "./styles/paraxe-preset.css";
import "./styles/paraxe-theme.css";
import "./styles/paraxe-overrides.css";
```

The preset imports its recipe. Project overrides load last. Importing another component baseline afterwards can undo recipe treatment. The CLI preserves an existing overrides file when regenerating.
