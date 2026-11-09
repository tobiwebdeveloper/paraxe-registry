# Choice

Choice is a public Vue and React component. Its shared API is defined by `ChoiceProps` from `@paraxe/core`.

## When to use it

Use Choice when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Choice to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Choice } from "@paraxe/vue";
```
```tsx
import { Choice } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `value` | `string | number` | -- | Yes | Defined by the core contract. |
| `disabled` | `boolean` | false | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Choice } from "@paraxe/vue";
</script>

<template>
  <Choice :value="value">Content</Choice>
</template>
```

### React

```tsx
import { Choice } from "@paraxe/react";

export function Example() {
  return <Choice value={value}>Content</Choice>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)


## Flexible composition

Use `Flex` inside ChoiceGroup to arrange choices in rows/columns. Choice supports `width="auto"` (default is full) and `size="small|medium|large"` (default medium). ChoiceGroup accepts `label` for its accessible group name. Compose a decorative Swatch plus visible text inside a Choice for color selection. Group/choice semantics remain toggle buttons; multi-select filters use `multiple`. Headings, counts, empty states, and filter placement belong to the registry block.
