# Input

Development also forwards minlength/maxlength/pattern. Invalid fields use the error appearance as well as aria-invalid, taking precedence over success.

Development adds native `min`, `max`, and `step` forwarding in Vue and React for numeric/date controls. Values may be strings or numbers. Browser constraints help entry; the application must still validate submissions. See [Stay01](../registry/stay-01.md) and [release status](../reference/release-status.md).

Input is a public Vue and React component. Its shared API is defined by `InputProps` from `@paraxe/core`.

## When to use it

Use Input when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Input to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Input } from "@paraxe/vue";
```
```tsx
import { Input } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | `string` | {id | No | Defined by the core contract. |
| `name` | `string` | {name | No | Defined by the core contract. |
| `autocomplete` | `string` | -- | No | Defined by the core contract. |
| `type` | `| "text" | "email" | "password" | "number" | "tel" | "url" | "search" | "date" | "time" | "datetime-local" | "month" | "week"` | "text" | No | Defined by the core contract. |
| `placeholder` | `string` | "" | No | Defined by the core contract. |
| `modelValue` | `string` | "" | No | Defined by the core contract. |
| `required` | `boolean` | false | No | Defined by the core contract. |
| `disabled` | `boolean` | false | No | Defined by the core contract. |
| `readonly` | `boolean` | false | No | Defined by the core contract. |
| `error` | `boolean` | false | No | Defined by the core contract. |
| `success` | `boolean` | false | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Input } from "@paraxe/vue";
</script>

<template>
  <Input>Content</Input>
</template>
```

### React

```tsx
import { Input } from "@paraxe/react";

export function Example() {
  return <Input>Content</Input>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)


## Plain treatment and validation

`variant="plain"` removes the visual border/fill for a composed toolbar or search field; default retains the normal input treatment. The component retains native focus behavior. `describedBy` maps to aria-describedby and `invalid` maps to aria-invalid (the existing error state also sets it). Use these to associate visible form errors, as Login01 does. Colors, typography, padding and minimum height come from the selected recipe and preset.
