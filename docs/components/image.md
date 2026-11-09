# Image

Image is a public Vue and React component. Its shared API is defined by `ImageProps` from `@paraxe/core`.

## When to use it

Use Image when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Image to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import

```ts
import { Image } from "@paraxe/vue";
```
```tsx
import { Image } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `src` | `string` | {src | Yes | Defined by the core contract. |
| `alt` | `string` | {alt | Yes | Defined by the core contract. |
| `fit` | `ImageFit` | "cover" | No | Defined by the core contract. |
| `aspectRatio` | `ImageAspectRatio` | "auto" | No | Defined by the core contract. |



## Usage

### Vue

```vue
<script setup lang="ts">
import { Image } from "@paraxe/vue";
</script>

<template>
  <Image :src="value">Content</Image>
</template>
```

### React

```tsx
import { Image } from "@paraxe/react";

export function Example() {
  return <Image src={value}>Content</Image>;
}
```

## Accessibility

`alt` is required and is passed to the rendered `img`.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)

## Development loading and fallback support

Image now accepts optional `src`, `pending`, `fallbackText`, and `loading` (`eager` by default or `lazy`). Missing or failed media displays a labelled placeholder. Changing the source resets the failure state. Pending media reserves its wrapper and announces busy state. Empty alt text keeps decorative fallback content hidden from assistive technology. These additions are staged for the next core/framework/design release.

Development correction: square, video, wide, and portrait media now read their existing `--media-aspect-*` tokens. Consumers can change those proportions without replacing component CSS.
