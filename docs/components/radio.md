# Radio

Radio is a public Vue and React component. Its shared API is defined by `RadioProps` from `@paraxe/core`.

## When to use it

Use Radio when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Radio to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Radio } from "@paraxe/vue";
```
```tsx
import { Radio } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `modelValue` | `string | number | null` | null | No | Defined by the core contract. |
| `value` | `string | number` | {value | Yes | Defined by the core contract. |
| `name` | `string` | {name | Yes | Defined by the core contract. |
| `disabled` | `boolean` | false | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Radio } from "@paraxe/vue";
</script>

<template>
  <Radio :value="value">Content</Radio>
</template>
```

### React

```tsx
import { Radio } from "@paraxe/react";

export function Example() {
  return <Radio value={value}>Content</Radio>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
