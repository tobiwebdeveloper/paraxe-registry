# Stack

Stack is a public Vue and React component. Its shared API is defined by `StackProps` from `@paraxe/core`.

## When to use it

Use Stack when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Stack to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Stack } from "@paraxe/vue";
```
```tsx
import { Stack } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `size` | `StackSize` | "medium" | No | Defined by the core contract. |
| `fullWidth` | `boolean` | false | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Stack } from "@paraxe/vue";
</script>

<template>
  <Stack>Content</Stack>
</template>
```

### React

```tsx
import { Stack } from "@paraxe/react";

export function Example() {
  return <Stack>Content</Stack>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
