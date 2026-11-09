# Label

Label is a public Vue and React component. Its shared API is defined by `LabelProps` from `@paraxe/core`.

## When to use it

Use Label when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Label to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Label } from "@paraxe/vue";
```
```tsx
import { Label } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `for` | `string` | -- | No | Defined by the core contract. |
| `required` | `boolean` | false | No | Defined by the core contract. |
| `optional` | `boolean` | false | No | Defined by the core contract. |
| `disabled` | `boolean` | false | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Label } from "@paraxe/vue";
</script>

<template>
  <Label>Content</Label>
</template>
```

### React

```tsx
import { Label } from "@paraxe/react";

export function Example() {
  return <Label>Content</Label>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
