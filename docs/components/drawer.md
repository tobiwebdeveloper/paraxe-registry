# Drawer

Drawer is a public Vue and React component. Its shared API is defined by `DrawerProps` from `@paraxe/core`.

## When to use it

Use Drawer when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Drawer to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Drawer } from "@paraxe/vue";
```
```tsx
import { Drawer } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `modelValue` | `boolean` | false | No | Defined by the core contract. |
| `side` | `"left" | "right"` | "right" | No | Defined by the core contract. |
| `closeOnBackdrop` | `boolean` | true | No | Defined by the core contract. |
| `closeOnEscape` | `boolean` | true | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Drawer } from "@paraxe/vue";
</script>

<template>
  <Drawer>Content</Drawer>
</template>
```

### React

```tsx
import { Drawer } from "@paraxe/react";

export function Example() {
  return <Drawer>Content</Drawer>;
}
```

## Accessibility

Rendered as a modal dialog. Escape and backdrop behaviour follow `closeOnEscape` and `closeOnBackdrop`; supply focusable, meaningful content.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
