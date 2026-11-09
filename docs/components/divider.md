# Divider

This component renders a decorative `div.divider` with `aria-hidden="true"`. It has no public props contract.

## When to use it

Use Divider when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Divider to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Divider } from "@paraxe/vue";
```
```tsx
import { Divider } from "@paraxe/react";
```

## Props

No public props are declared for this component.



## Usage

### Vue

```vue
<script setup lang="ts">
import { Divider } from "@paraxe/vue";
</script>

<template>
  <Divider>Content</Divider>
</template>
```

### React

```tsx
import { Divider } from "@paraxe/react";

export function Example() {
  return <Divider>Content</Divider>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
