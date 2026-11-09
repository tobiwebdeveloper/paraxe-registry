# EmptyState

EmptyState is a public Vue and React component. Its shared API is defined by `EmptyStateProps` from `@paraxe/core`.

## When to use it

Use EmptyState when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use EmptyState to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { EmptyState } from "@paraxe/vue";
```
```tsx
import { EmptyState } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `as` | `string` | "div" | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { EmptyState } from "@paraxe/vue";
</script>

<template>
  <EmptyState>Content</EmptyState>
</template>
```

### React

```tsx
import { EmptyState } from "@paraxe/react";

export function Example() {
  return <EmptyState>Content</EmptyState>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
