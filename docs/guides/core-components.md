# Build with core components

Import rendering components from `@paraxe/vue` or `@paraxe/react`. Import shared contracts/helpers from `@paraxe/core` when needed. Start with the [component index](../reference/component-index.md), then verify the installed exports/declarations.

Use Flex for rows, columns, wrapping, alignment, and gaps. Use Grid for genuinely two-dimensional layouts. Container/Section establish page structure; Card groups a surface. Choose Heading levels for the document hierarchy, not simply their size.

## A complete local example

Vue:

```vue
<script setup lang="ts">
import { ref } from "vue";
import { Button, Card, Flex, Heading, Text } from "@paraxe/vue";
const count = ref(0);
</script>
<template>
  <Card>
    <Flex direction="column" size="medium">
      <Heading level="h2">Project notes</Heading>
      <Text>{{ count }} notes added in this local example.</Text>
      <Button @activate="count += 1">Add a note</Button>
    </Flex>
  </Card>
</template>
```

React:

```tsx
import { useState } from "react";
import { Button, Card, Flex, Heading, Text } from "@paraxe/react";

export function ProjectNotes() {
  const [count, setCount] = useState(0);
  return (
    <Card>
      <Flex direction="column" size="medium">
        <Heading level="h2">Project notes</Heading>
        <Text>{count} notes added in this local example.</Text>
        <Button onActivate={() => setCount(value => value + 1)}>
          Add a note
        </Button>
      </Flex>
    </Card>
  );
}
```

Both require [application CSS setup](install-and-theme.md). This state remains local; the button does not persist anything.

## Use the actual API

| Task | Vue | React |
| --- | --- | --- |
| Button activation | `@activate` | `onActivate` |
| Controlled value | `v-model` / `update:modelValue` | `modelValue` + `onModelValueChange` where implemented |
| Variant defaults | `createParaxe({ variants })` | `ParaxeProvider` |

Do not mechanically translate DOM events or assume every wrapper forwards native attributes. Installed declarations and framework source are authoritative. The [current contract snapshot](../reference/current-contracts.md) describes development source.

Pair inputs with visible labels and stable IDs. The app owns values, validation, pending, failure, and submission. Use the installed version's documented helper APIs; recent FormField targets and Select validity props are development additions. Native helper markup can supply IDs when an older wrapper cannot.

Use links for real navigation and buttons for actions. Preserve rejected drafts, prevent duplicate requests while pending, and announce useful feedback. Server validation, auth, persistence, and transport belong to the app.

Let recipes supply type/control treatment and presets choose brand, fonts, radius, density, surfaces, and variants. Scope composition CSS, consume semantic tokens, and put complete custom styling in the project override layer. Do not edit generated files or node_modules as the lasting fix.

Verify empty, unavailable, long-text, loading/failure, and narrow-screen states. Typecheck/build and test meaningful behavior. Compilation does not prove visual balance or keyboard accessibility.

