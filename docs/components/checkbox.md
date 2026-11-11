# Checkbox

A native boolean checkbox with a labelled visual control. Import Checkbox from @paraxe/vue or @paraxe/react. Its shared CheckboxProps contract lives in @paraxe/core.

| Prop | Type | Default | Purpose |
| --- | --- | --- | --- |
| modelValue | boolean | false | Current checked state |
| name | string | Omitted | Native form name |
| disabled | boolean | false | Disable input |
| required | boolean | false | Native required constraint |
| id | string | Omitted | Native input ID |
| labelledBy | string | Omitted | Accessible label IDs |
| describedBy | string | Omitted | Space-separated help/error IDs |
| invalid | boolean | false | aria-invalid and error border |

id, labelledBy, describedBy, and invalid ship in core 1.6.0, Vue 1.5.0, and React 0.4.0.

```vue
<script setup lang="ts">
import { ref } from 'vue';
import { Checkbox } from '@paraxe/vue';
const accepted = ref(false);
</script>
<template>
  <Checkbox v-model="accepted" id="terms" described-by="terms-help">
    Accept the terms
  </Checkbox>
  <p id="terms-help">Required to create your account.</p>
</template>
```

```tsx
import { useState } from 'react';
import { Checkbox } from '@paraxe/react';
function Terms() {
  const [accepted, setAccepted] = useState(false);
  return <>
    <Checkbox id="terms" modelValue={accepted}
      onModelValueChange={setAccepted} describedBy="terms-help">
      Accept the terms
    </Checkbox>
    <p id="terms-help">Required to create your account.</p>
  </>;
}
```

Use slot/children text for a normal label. For external labels supply labelledBy and matching IDs. Link errors through describedBy and set invalid; announce request failures in the owning form. Controlled state belongs to the application. Checkbox has no indeterminate state; core Table manages its own native mixed-selection input. Preset form/control roles determine size, border, radius, text, and checked treatment.

See [Dashboard01](../registry/dashboard-01.md) for descriptions, pending changes, and linked save failures.
