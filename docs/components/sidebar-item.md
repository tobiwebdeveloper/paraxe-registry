# SidebarItem

SidebarItem is a public Vue and React component. Its shared API is defined by `SidebarProps` from `@paraxe/core`.

## When to use it

Use SidebarItem when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use SidebarItem to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { SidebarItem } from "@paraxe/vue";
```
```tsx
import { SidebarItem } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `collapsed` | `boolean` | -- | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { SidebarItem } from "@paraxe/vue";
</script>

<template>
  <SidebarItem>Content</SidebarItem>
</template>
```

### React

```tsx
import { SidebarItem } from "@paraxe/react";

export function Example() {
  return <SidebarItem>Content</SidebarItem>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
