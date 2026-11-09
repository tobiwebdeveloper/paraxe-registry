# List

List is a public Vue and React component. Its shared API is defined by `ListProps` from `@paraxe/core`.

## When to use it

Use List when its semantic structure and contract match the interface pattern. Use with `ListItem`. Selection is enabled only when `selectable` is true.

## When not to use it

Do not use List to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { List } from "@paraxe/vue";
```
```tsx
import { List } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `selectable` | `boolean` | false | No | Defined by the core contract. |
| `multiple` | `boolean` | false | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { List } from "@paraxe/vue";
</script>

<template>
  <List>Content</List>
</template>
```

### React

```tsx
import { List } from "@paraxe/react";

export function Example() {
  return <List>Content</List>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
