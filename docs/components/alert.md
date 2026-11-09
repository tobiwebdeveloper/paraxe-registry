# Alert

Alert is a public Vue and React component. Its shared API is defined by `AlertProps` from `@paraxe/core`.

## When to use it

Use Alert when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Alert to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Alert } from "@paraxe/vue";
```
```tsx
import { Alert } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `variant` | `AlertVariant` | "info" | No | Defined by the core contract. |
| `dismissible` | `boolean` | false | No | Defined by the core contract. |

## Events

| Event | Payload | Description |
| --- | --- | --- |
| `close` / `onClose()` | See framework implementation | Emitted/called by the documented interaction. |

## Usage

### Vue

```vue
<script setup lang="ts">
import { Alert } from "@paraxe/vue";
</script>

<template>
  <Alert>Content</Alert>
</template>
```

### React

```tsx
import { Alert } from "@paraxe/react";

export function Example() {
  return <Alert>Content</Alert>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
