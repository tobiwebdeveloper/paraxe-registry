# Menu

This React-only export renders a `nav.menu` around its children. It has no public props contract.

## When to use it

Use Menu when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Menu to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Menu } from "@paraxe/vue";
```
```tsx
import { Menu } from "@paraxe/react";
```

## Props

No public props are declared for this component.



## Usage

### Vue

```vue
<script setup lang="ts">
import { Menu } from "@paraxe/vue";
</script>

<template>
  <Menu>Content</Menu>
</template>
```

### React

```tsx
import { Menu } from "@paraxe/react";

export function Example() {
  return <Menu>Content</Menu>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
