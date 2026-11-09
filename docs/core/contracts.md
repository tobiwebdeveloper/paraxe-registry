# Component contracts

Core contracts are TypeScript interfaces and unions exported from `@paraxe/core`. They define shared prop vocabulary, not component instances. Vue implements two-way values through `v-model` / `update:modelValue`; React uses explicit callback props such as `onModelValueChange` where implemented.

Use the [contract source reference](../reference/contracts.md) for exact exported type declarations. Component pages render their corresponding prop table from the same source files.
