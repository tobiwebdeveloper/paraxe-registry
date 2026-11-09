# Toast

Toast is a public Vue and React component. Its shared API is defined by `ToastProps` from `@paraxe/core`.

## When to use it

Use Toast when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Toast to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Toast } from "@paraxe/vue";
```
```tsx
import { Toast } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `modelValue` | `boolean` | false | No | Defined by the core contract. |
| `title` | `string` | -- | No | Defined by the core contract. |
| `variant` | `ToastVariant` | "info" | No | Defined by the core contract. |
| `duration` | `number` | 4000 | No | Defined by the core contract. |
| `dismissible` | `boolean` | true | No | Defined by the core contract. |

## Events

| Event | Payload | Description |
| --- | --- | --- |
| `update:modelValue`, `close` / `onModelValueChange`, `onClose` | See framework implementation | Emitted/called by the documented interaction. |

## Usage

### Vue

```vue
<script setup lang="ts">
import { Toast } from "@paraxe/vue";
</script>

<template>
  <Toast>Content</Toast>
</template>
```

### React

```tsx
import { Toast } from "@paraxe/react";

export function Example() {
  return <Toast>Content</Toast>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
