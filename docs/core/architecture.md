# Core architecture

```text
@paraxe/core
      ↓
contracts / shared types
      ↓
┌──────────────┬──────────────┐
│ @paraxe/vue  │ @paraxe/react│
└──────────────┴──────────────┘
      ↓
@paraxe/design CSS tokens, themes, presets, component styles
```

The core package deliberately contains contracts rather than DOM implementations. This lets Vue and React use the same vocabulary for variants, sizes, and model values while retaining framework-native rendering and events. The CSS design package is separately importable so applications can use tokens without importing a component runtime.

Some framework exports do not have a core contract, and not every source file is exported by every framework. That is a repository fact, not a compatibility guarantee; see [packages and exports](../reference/packages.md).
