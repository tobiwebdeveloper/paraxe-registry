# Stat

Stat presents a labelled value with an optional comparison. Import Stat from @paraxe/vue or @paraxe/react. It is a focused core component. React support and updated surface roles are development after published React 0.3.0/design 1.9.0.

| Prop | Type | Default |
| --- | --- | --- |
| label | string | Required |
| value | string or number | Required |
| change | string | Omitted |
| trend | up, down, neutral | neutral |
| variant | default, plain | Provider choice or default |

Default uses card padding, background, border, shadow, and radius tokens. Plain removes the surface and padding. Both use shared typography. VariantProvider can select the stat variant. React accepts className/style; Vue inherits attributes.

```vue
<script setup lang="ts">
import { Stat } from '@paraxe/vue';
</script>
<template>
  <Stat label="Projects delivered" :value="12" />
</template>
```

```tsx
import { Stat } from '@paraxe/react';
<Stat label="Projects delivered" value={12} />
```

Supply change and trend only for meaningful comparisons, such as change="2 more than last month" and trend="up". Direction does not imply that more is always better. Explain context when necessary; omit comparison when no baseline is known. See [Dashboard01](../registry/dashboard-01.md) for a complete layout.
