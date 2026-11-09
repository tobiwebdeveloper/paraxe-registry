# Table

Table is a public Vue and React component. Its shared API is defined by `TableProps` from `@paraxe/core`.

## When to use it

Use Table when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Table to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Table } from "@paraxe/vue";
```
```tsx
import { Table } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `columns` | `TableColumn<T>[]` | -- | Yes | Defined by the core contract. |
| `rows` | `T[]` | -- | Yes | Defined by the core contract. |
| `rowKey` | `string` | "id" | No | Defined by the core contract. |
| `sortable` | `boolean` | false | No | Defined by the core contract. |
| `selectable` | `boolean` | false | No | Defined by the core contract. |
| `multiple` | `boolean` | false | No | Defined by the core contract. |
| `loading` | `boolean` | false | No | Defined by the core contract. |
| `empty` | `boolean` | -- | No | Defined by the core contract. |

## Events

| Event | Payload | Description |
| --- | --- | --- |
| `update:selectedRows`, `sort`, `row-click` / `onSelectedRowsChange`, `onSort`, `onRowClick` | See framework implementation | Emitted/called by the documented interaction. |

## Usage

### Vue

```vue
<script setup lang="ts">
import { Table } from "@paraxe/vue";
</script>

<template>
  <Table :columns="value">Content</Table>
</template>
```

### React

```tsx
import { Table } from "@paraxe/react";

export function Example() {
  return <Table columns={value}>Content</Table>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
