# Flex

Flex arranges content in a row or column with shared spacing tokens. Use Grid for aligned columns; use Stack for a simple vertical group. Flex adds wrapping, cross-axis alignment, and distribution without changing reading or keyboard order.

```vue
<script setup lang="ts">
import { Flex, Button } from "@paraxe/vue";
</script>

<template>
  <Flex align="center" justify="between" wrap>
    <span>12 products</span>
    <Button>Filter products</Button>
  </Flex>
</template>
```

```tsx
import { Flex, Button } from "@paraxe/react";

export function Toolbar() {
  return (
    <Flex align="center" justify="between" wrap>
      <span>12 products</span>
      <Button>Filter products</Button>
    </Flex>
  );
}
```

| Prop | Values | Default |
| --- | --- | --- |
| as | div, span | div |
| inline | boolean | false |
| direction | row, column | row |
| wrap | boolean | false |
| align | stretch, start, center, end, baseline | stretch |
| justify | start, center, end, between, around, evenly | start |
| size | small, medium, large | medium |
| fullWidth | boolean | false |

`size` controls gaps through `--stack-gap-sm`, `--stack-gap`, and `--stack-gap-lg`, so it follows generated density settings. Override these roles on a wrapper for local customization. Standard HTML attributes and classes pass to the root div in both frameworks. Flex adds no interactive semantics; supply meaningful native children and labels. Wrapping is opt-in and retains source order. Long unbreakable content may still need application-specific wrapping rules.
