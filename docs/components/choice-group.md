# ChoiceGroup

ChoiceGroup is a public Vue and React component. Its shared API is defined by `ChoiceGroupProps` from `@paraxe/core`.

## When to use it

Use ChoiceGroup when its semantic structure and contract match the interface pattern. Use with `Choice`. The group provides selection state to its child choices.

## When not to use it

Do not use ChoiceGroup to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { ChoiceGroup } from "@paraxe/vue";
```
```tsx
import { ChoiceGroup } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `modelValue` | `| string | number | Array<string | number> | null` | null | No | Defined by the core contract. |
| `multiple` | `boolean` | false | No | Defined by the core contract. |
| `disabled` | `boolean` | false | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { ChoiceGroup } from "@paraxe/vue";
</script>

<template>
  <ChoiceGroup>Content</ChoiceGroup>
</template>
```

### React

```tsx
import { ChoiceGroup } from "@paraxe/react";

export function Example() {
  return <ChoiceGroup>Content</ChoiceGroup>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)


## Flexible composition

Use `Flex` inside ChoiceGroup to arrange choices in rows/columns. Choice supports `width="auto"` (default is full) and `size="small|medium|large"` (default medium). ChoiceGroup accepts `label` for its accessible group name. Compose a decorative Swatch plus visible text inside a Choice for color selection. Group/choice semantics remain toggle buttons; multi-select filters use `multiple`. Headings, counts, empty states, and filter placement belong to the registry block.
