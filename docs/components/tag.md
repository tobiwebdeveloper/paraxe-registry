# Tag

This component renders a `span.tag` around its children. It has no public props contract.

## When to use it

Use Tag when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Tag to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Tag } from "@paraxe/vue";
```
```tsx
import { Tag } from "@paraxe/react";
```

## Props

No public props are declared for this component.



## Usage

### Vue

```vue
<script setup lang="ts">
import { Tag } from "@paraxe/vue";
</script>

<template>
  <Tag>Content</Tag>
</template>
```

### React

```tsx
import { Tag } from "@paraxe/react";

export function Example() {
  return <Tag>Content</Tag>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
