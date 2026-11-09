# SectionHeader

SectionHeader is a public Vue and React component. Its shared API is defined by `SectionHeaderProps` from `@paraxe/core`.

## When to use it

Use SectionHeader when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use SectionHeader to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { SectionHeader } from "@paraxe/vue";
```
```tsx
import { SectionHeader } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `width` | `SectionHeaderWidth` | "default" | No | Defined by the core contract. |
| `align` | `SectionHeaderAlign` | "left" | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { SectionHeader } from "@paraxe/vue";
</script>

<template>
  <SectionHeader>Content</SectionHeader>
</template>
```

### React

```tsx
import { SectionHeader } from "@paraxe/react";

export function Example() {
  return <SectionHeader>Content</SectionHeader>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
