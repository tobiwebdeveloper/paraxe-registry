# Sidebar

Sidebar is a public Vue and React component. Its shared API is defined by `SidebarProps` from `@paraxe/core`.

## When to use it

Use Sidebar when its semantic structure and contract match the interface pattern. Use with `SidebarGroup` and `SidebarItem` to build navigation.

## When not to use it

Do not use Sidebar to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Sidebar } from "@paraxe/vue";
```
```tsx
import { Sidebar } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `collapsed` | `boolean` | false | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Sidebar } from "@paraxe/vue";
</script>

<template>
  <Sidebar>Content</Sidebar>
</template>
```

### React

```tsx
import { Sidebar } from "@paraxe/react";

export function Example() {
  return <Sidebar>Content</Sidebar>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
