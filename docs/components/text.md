# Text

Text is a public Vue and React component. Its shared API is defined by `TextProps` from `@paraxe/core`.

## When to use it

Use Text when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Text to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Text } from "@paraxe/vue";
```
```tsx
import { Text } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `as` | `TextElement` | "p" | No | Defined by the core contract. |
| `tone` | `TextTone` | "primary" | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Text } from "@paraxe/vue";
</script>

<template>
  <Text>Content</Text>
</template>
```

### React

```tsx
import { Text } from "@paraxe/react";

export function Example() {
  return <Text>Content</Text>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)

## Development accessibility update

React Text now forwards native and ARIA attributes, including id, to its rendered element, matching Vue attribute fallthrough. These changes are staged for the next coordinated package release.
