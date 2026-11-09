# Button

Button is a public Vue and React component. Its shared API is defined by `ButtonProps` from `@paraxe/core`.

## When to use it

Use Button when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Button to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Button } from "@paraxe/vue";
```
```tsx
import { Button } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `variant` | `ButtonVariant` | "primary" | No | Defined by the core contract. |
| `size` | `ButtonSize` | "medium" | No | Defined by the core contract. |
| `width` | `ButtonWidth` | "auto" | No | Defined by the core contract. |
| `iconPosition` | `ButtonIconPosition` | -- | No | Defined by the core contract. |
| `disabled` | `boolean` | false | No | Defined by the core contract. |
| `loading` | `boolean` | false | No | Defined by the core contract. |

## Events

| Event | Payload | Description |
| --- | --- | --- |
| `activate` / `onActivate()` | See framework implementation | Emitted/called by the documented interaction. |

## Usage

### Vue

```vue
<script setup lang="ts">
import { Button } from "@paraxe/vue";
</script>

<template>
  <Button>Content</Button>
</template>
```

### React

```tsx
import { Button } from "@paraxe/react";

export function Example() {
  return <Button>Content</Button>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)


## Form type and styling

`type` accepts button (default), submit, or reset in both frameworks. Use submit inside a form; action buttons remain button by default. `variant="text"` supplies an underlined action using the shared tokens. Component recipes and the final project override file can replace its complete visual treatment without changing button semantics.
