# Progress

Progress is a public Vue and React component. Its shared API is defined by `ProgressProps` from `@paraxe/core`.

## When to use it

Use Progress when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Progress to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Progress } from "@paraxe/vue";
```
```tsx
import { Progress } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `value` | `number` | 0 | No | Defined by the core contract. |
| `max` | `number` | 100 | No | Defined by the core contract. |
| `indeterminate` | `boolean` | false | No | Defined by the core contract. |
| `variant` | `ProgressVariant` | "default" | No | Defined by the core contract. |
| `showValue` | `boolean` | false | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Progress } from "@paraxe/vue";
</script>

<template>
  <Progress>Content</Progress>
</template>
```

### React

```tsx
import { Progress } from "@paraxe/react";

export function Example() {
  return <Progress>Content</Progress>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)

## Development accessibility update

`label` supplies the progressbar's accessible name in Vue and React. Determinate `value` is clamped to `0..max` for both the visual bar and ARIA. `max` must be finite and positive; `value` must be finite. Invalid determinate configurations throw RangeError. Indeterminate progress omits value attributes. These changes are staged for the next package release.
