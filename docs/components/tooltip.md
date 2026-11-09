# Tooltip

Tooltip is a public Vue and React component. Its shared API is defined by `TooltipProps` from `@paraxe/core`.

## When to use it

Use Tooltip when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Tooltip to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Tooltip } from "@paraxe/vue";
```
```tsx
import { Tooltip } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `placement` | `TooltipPlacement` | "top" | No | Defined by the core contract. |
| `text` | `string` | createContext<{ | Yes | Defined by the core contract. |
| `delay` | `number` | 300 | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Tooltip } from "@paraxe/vue";
</script>

<template>
  <Tooltip :text="value">Content</Tooltip>
</template>
```

### React

```tsx
import { Tooltip } from "@paraxe/react";

export function Example() {
  return <Tooltip text={value}>Content</Tooltip>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
