# Heading

Heading is a public Vue and React component. Its shared API is defined by `HeadingProps` from `@paraxe/core`.

## When to use it

Use Heading when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Heading to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Heading } from "@paraxe/vue";
```
```tsx
import { Heading } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `level` | `HeadingLevel` | "h2" | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Heading } from "@paraxe/vue";
</script>

<template>
  <Heading>Content</Heading>
</template>
```

### React

```tsx
import { Heading } from "@paraxe/react";

export function Example() {
  return <Heading>Content</Heading>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)

## Development heading weight roles

The Heading scale consumes `--typography-heading-xs-weight` through `--typography-heading-xl-weight`. Defaults preserve the existing semibold extra-small and bold larger headings. Studio sets all five roles from its regular-weight heading role, keeping its lighter display treatment effective. Other recipes retain their current weights.
