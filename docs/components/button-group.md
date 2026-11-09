# ButtonGroup

ButtonGroup is a public Vue and React component. Its shared API is defined by `ButtonGroupProps` from `@paraxe/core`.

## When to use it

Use ButtonGroup when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use ButtonGroup to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { ButtonGroup } from "@paraxe/vue";
```
```tsx
import { ButtonGroup } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `align` | `ButtonGroupAlign` | "start" | No | Defined by the core contract. |
| `stack` | `boolean` | false | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { ButtonGroup } from "@paraxe/vue";
</script>

<template>
  <ButtonGroup>Content</ButtonGroup>
</template>
```

### React

```tsx
import { ButtonGroup } from "@paraxe/react";

export function Example() {
  return <ButtonGroup>Content</ButtonGroup>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
