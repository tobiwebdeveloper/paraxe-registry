# Pagination

Pagination is a public Vue and React component. Its shared API is defined by `PaginationProps` from `@paraxe/core`.

## When to use it

Use Pagination when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Pagination to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Pagination } from "@paraxe/vue";
```
```tsx
import { Pagination } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `currentPage` | `number` | -- | Yes | Defined by the core contract. |
| `totalItems` | `number` | -- | Yes | Defined by the core contract. |
| `pageSize` | `number` | -- | Yes | Defined by the core contract. |
| `siblingCount` | `number` | 1 | No | Defined by the core contract. |
| `compact` | `boolean` | false | No | Defined by the core contract. |

## Events

| Event | Payload | Description |
| --- | --- | --- |
| `update:currentPage` / `onCurrentPageChange` | See framework implementation | Emitted/called by the documented interaction. |

## Usage

### Vue

```vue
<script setup lang="ts">
import { Pagination } from "@paraxe/vue";
</script>

<template>
  <Pagination :current-page="value">Content</Pagination>
</template>
```

### React

```tsx
import { Pagination } from "@paraxe/react";

export function Example() {
  return <Pagination currentPage={value}>Content</Pagination>;
}
```

## Accessibility

This component supplies some interaction ARIA in its implementation. Provide meaningful child labels and preserve the required parent/child relationship.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
