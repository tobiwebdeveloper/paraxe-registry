# ListItem

ListItem is a public Vue and React component. Its shared API is defined by `ListProps` from `@paraxe/core`.

## When to use it

Use ListItem when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use ListItem to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { ListItem } from "@paraxe/vue";
```
```tsx
import { ListItem } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `selectable` | `boolean` | -- | No | Defined by the core contract. |
| `multiple` | `boolean` | -- | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { ListItem } from "@paraxe/vue";
</script>

<template>
  <ListItem>Content</ListItem>
</template>
```

### React

```tsx
import { ListItem } from "@paraxe/react";

export function Example() {
  return <ListItem>Content</ListItem>;
}
```

## Accessibility

This component supplies some interaction ARIA in its implementation. Provide meaningful child labels and preserve the required parent/child relationship.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
