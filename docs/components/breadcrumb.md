# Breadcrumb

Breadcrumb is a public Vue and React component. Its shared API is defined by `BreadcrumbProps` from `@paraxe/core`.

## When to use it

Use Breadcrumb when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Breadcrumb to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Breadcrumb } from "@paraxe/vue";
```
```tsx
import { Breadcrumb } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `href` | `string` | {href | No | Defined by the core contract. |
| `current` | `boolean` | false | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Breadcrumb } from "@paraxe/vue";
</script>

<template>
  <Breadcrumb>Content</Breadcrumb>
</template>
```

### React

```tsx
import { Breadcrumb } from "@paraxe/react";

export function Example() {
  return <Breadcrumb>Content</Breadcrumb>;
}
```

## Accessibility

This component supplies some interaction ARIA in its implementation. Provide meaningful child labels and preserve the required parent/child relationship.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
