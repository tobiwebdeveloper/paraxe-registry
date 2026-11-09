# Tab

Tab is a public Vue and React component. Its shared API is defined by `TabProps` from `@paraxe/core`.

## When to use it

Use Tab when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Tab to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Tab } from "@paraxe/vue";
```
```tsx
import { Tab } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `value` | `string | number` | {{ active | Yes | Defined by the core contract. |
| `disabled` | `boolean` | false | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Tab } from "@paraxe/vue";
</script>

<template>
  <Tab :value="value">Content</Tab>
</template>
```

### React

```tsx
import { Tab } from "@paraxe/react";

export function Example() {
  return <Tab value={value}>Content</Tab>;
}
```

## Accessibility

This component supplies some interaction ARIA in its implementation. Provide meaningful child labels and preserve the required parent/child relationship.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
