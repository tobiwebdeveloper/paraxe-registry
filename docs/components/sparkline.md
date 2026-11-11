# Sparkline

A small SVG trend or bar sequence. Import Sparkline from @paraxe/vue or @paraxe/react. React support, explicit scale bounds, and shared geometry ship with core 1.6.0, Vue 1.5.0, and React 0.4.0.

| Prop | Type | Default |
| --- | --- | --- |
| data | number[] | Required |
| variant | line, area, bars | Provider choice or line |
| width / height | number | 96 / 32 |
| min / max | number | Observed data bounds (bars include zero) |
| color | CSS color | chart-color-1 token |
| trend | boolean | false |
| label | string | Omitted; decorative SVG |

Use min and max for fair comparisons across multiple trends or bounded percentages. A percentage chart normally uses 0 and 100. Data must be finite; dimensions must be at least 4 and explicit bounds must increase. Out-of-range samples clamp to the supplied scale. Line/area segments preserve the samples without smoothing overshoot. Bars extend from zero when it falls inside the scale, or from the closest scale edge otherwise. Negative-only bars extend downward toward the samples. Empty data produces no marks; applications should provide a meaningful empty state.

```tsx
import { Sparkline } from '@paraxe/react';
<Sparkline data={[20, 32, 41, 57]} min={0} max={100}
  variant="area" color="var(--brand-primary)" label="Delivery completion over four reporting dates" />
```

```vue
<script setup lang="ts">
import { Sparkline } from '@paraxe/vue';
</script>
<template>
  <Sparkline :data="[20, 32, 41, 57]" :min="0" :max="100"
    variant="area" color="var(--brand-primary)"
    label="Delivery completion over four reporting dates" />
</template>
```

Colour defaults and positive/negative trend colours use chart tokens. React accepts className/style; Vue accepts inherited SVG attributes. Give meaningful charts a label and provide readable values when exact data matters. Unlabelled charts are decorative. Sparkline has no axes, tooltip, or interaction; compose those where the domain needs them, or choose a full chart. See [Dashboard01](../registry/dashboard-01.md) for an explicit scale and an accessible reporting table.
