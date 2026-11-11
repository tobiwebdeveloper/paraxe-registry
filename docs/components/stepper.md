# Stepper

A read-only step indicator for a staged process. Vue and React now share the same progress model. React parity, the optional label, and bounded progress behaviour ship with core 1.6.0, Vue 1.5.0, and React 0.4.0.

| Prop | Type | Default |
| --- | --- | --- |
| steps | string[] | Required, nonempty labels |
| current | number | Required, zero-based active index |
| variant | default, dots, bars, vertical | Provider/preset choice or default |
| label | string | Progress |

```tsx
import { Stepper } from '@paraxe/react';
<Stepper steps={['Contact', 'Delivery', 'Review']} current={1} label="Checkout progress" />
```

```vue
<Stepper :steps="['Contact', 'Delivery', 'Review']" :current="1" label="Checkout progress" />
```

Import Stepper from @paraxe/vue for the Vue example. The ordered list names the process and marks exactly one existing item with aria-current=step. Markers are decorative. Repeated labels remain safe because entries use their index as identity. Empty steps produce an empty list. Finite current values truncate and clamp to the available range; nonfinite values fall back to the first step. The shared stepperSteps helper supplies label, index, and complete/current/upcoming status.

Stepper does not validate inputs, navigate, submit, or imply a completed transaction. Keep those operations in the owning flow, as in [Checkout01](../registry/checkout-01.md). React accepts className/style; Vue inherits attributes. Variant defaults use the existing preset catalogue and framework providers.
