# Switch

Switch is a public Vue and React component. Its shared API is defined by `SwitchProps` from `@paraxe/core`.

Development after registry 0.2.0 adds id, name, labelledBy, describedBy, required, and invalid to both frameworks. These attributes reach the native checkbox with role="switch"; invalid also selects the shared error border. Use a visible child label or an external label with labelledBy, and connect helper text with describedBy. See [Settings01](../registry/settings-01.md) for a complete preference-row example. These additions require matching development packages until the next npm release.

## When to use it

Use Switch when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Switch to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Switch } from "@paraxe/vue";
```
```tsx
import { Switch } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `modelValue` | `boolean` | false | No | Defined by the core contract. |
| `disabled` | `boolean` | false | No | Defined by the core contract. |
| `id` | `string` | — | No | Native input ID; development after 0.2.0. |
| `name` | `string` | — | No | Native form field name; development after 0.2.0. |
| `labelledBy` | `string` | — | No | ID of an external visible label; development after 0.2.0. |
| `describedBy` | `string` | — | No | IDs of helper/error text; development after 0.2.0. |
| `required` | `boolean` | false | No | Native required checkbox constraint; development after 0.2.0. |
| `invalid` | `boolean` | false | No | Announces invalid state and uses the shared error border; development after 0.2.0. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Switch } from "@paraxe/vue";
</script>

<template>
  <Switch>Content</Switch>
</template>
```

### React

```tsx
import { Switch } from "@paraxe/react";

export function Example() {
  return <Switch>Content</Switch>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
