# FormField

FormField is a public Vue and React component. Its shared API is defined by `FormFieldProps` from `@paraxe/core`.

## When to use it

Use FormField when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use FormField to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { FormField } from "@paraxe/vue";
```
```tsx
import { FormField } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | `string` | {id | No | Defined by the core contract. |
| `label` | `string` | -- | No | Defined by the core contract. |
| `description` | `string` | -- | No | Defined by the core contract. |
| `error` | `string` | false | No | Defined by the core contract. |
| `required` | `boolean` | false | No | Defined by the core contract. |
| `optional` | `boolean` | false | No | Defined by the core contract. |
| `disabled` | `boolean` | false | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { FormField } from "@paraxe/vue";
</script>

<template>
  <FormField>Content</FormField>
</template>
```

### React

```tsx
import { FormField } from "@paraxe/react";

export function Example() {
  return <FormField>Content</FormField>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)

## Development accessibility update

When id is supplied, descriptions and errors have id-description and id-error targets. Errors have an alert role and a semantic error colour. Consumers connect helper IDs through their control describedBy prop. These changes are staged for the next coordinated package release.
