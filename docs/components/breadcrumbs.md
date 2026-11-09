# Breadcrumbs

Breadcrumbs is a public Vue and React component. Its shared API is defined by `BreadcrumbsProps` from `@paraxe/core`.

## When to use it

Use Breadcrumbs when its semantic structure and contract match the interface pattern. Use with `Breadcrumb` children.

## When not to use it

Do not use Breadcrumbs to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Breadcrumbs } from "@paraxe/vue";
```
```tsx
import { Breadcrumbs } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `separator` | `string` | "/" | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Breadcrumbs } from "@paraxe/vue";
</script>

<template>
  <Breadcrumbs>Content</Breadcrumbs>
</template>
```

### React

```tsx
import { Breadcrumbs } from "@paraxe/react";

export function Example() {
  return <Breadcrumbs>Content</Breadcrumbs>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
