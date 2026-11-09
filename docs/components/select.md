# Select

Select is a public Vue and React component. Its shared API is defined by `SelectProps` from `@paraxe/core`.

## When to use it

Use Select when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Select to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Select } from "@paraxe/vue";
```
```tsx
import { Select } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | `string` | {id | No | Defined by the core contract. |
| `name` | `string` | {name | No | Defined by the core contract. |
| `modelValue` | `string` | "" | No | Defined by the core contract. |
| `disabled` | `boolean` | false | No | Defined by the core contract. |
| `error` | `boolean` | false | No | Defined by the core contract. |
| `success` | `boolean` | false | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Select } from "@paraxe/vue";
</script>

<template>
  <Select>Content</Select>
</template>
```

### React

```tsx
import { Select } from "@paraxe/react";

export function Example() {
  return <Select>Content</Select>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)


## Plain treatment

`variant="plain"` is a borderless native select for contexts such as a collection sort toolbar; default retains normal form treatment. Recipes can replace the visual treatment while native labels, options, keyboard and focus behavior remain intact.

## Development accessibility update

Select now exposes required, describedBy, and invalid in both frameworks, including native required and ARIA validity/description attributes. These changes are staged for the next coordinated package release.
