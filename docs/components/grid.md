# Grid

Grid is a public Vue and React component. Its shared API is defined by `GridProps` from `@paraxe/core`.

## When to use it

Use Grid when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Grid to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Grid } from "@paraxe/vue";
```
```tsx
import { Grid } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `columns` | `GridColumns` | 1 | No | Defined by the core contract. |
| `rows` | `GridRows` | 1 | No | Defined by the core contract. |
| `size` | `GridSize` | "medium" | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Grid } from "@paraxe/vue";
</script>

<template>
  <Grid>Content</Grid>
</template>
```

### React

```tsx
import { Grid } from "@paraxe/react";

export function Example() {
  return <Grid>Content</Grid>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)

## Alignment

`align` accepts `stretch` (default), `start`, `center`, or `end` in Vue and React. Stretch gives direct child cards equal heights within each row. Use `start` when each card should follow its own content height. It does not force equal heights across separate rows or resize a chart inside a card.

Vue: `<Grid :columns="3" align="stretch">...</Grid>`

React: `<Grid columns={3} align="stretch">...</Grid>`
