# Tabs

Tabs is a public Vue and React component. Its shared API is defined by `TabsProps` from `@paraxe/core`.

## When to use it

Use Tabs when its semantic structure and contract match the interface pattern. Use with `Tab`. A `Tab` outside `Tabs` throws at runtime.

## When not to use it

Do not use Tabs to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Tabs } from "@paraxe/vue";
```
```tsx
import { Tabs } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `modelValue` | `string | number | null` | null | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Tabs } from "@paraxe/vue";
</script>

<template>
  <Tabs>Content</Tabs>
</template>
```

### React

```tsx
import { Tabs } from "@paraxe/react";

export function Example() {
  return <Tabs>Content</Tabs>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
