# Fieldset

Groups related controls using native fieldset and legend elements. Available in development Vue and React source after registry 0.2.0; use matching development packages until the next coordinated release.

| Prop | Type | Default |
| --- | --- | --- |
| legend | string | Required |
| id | string | Generated stable ID |
| description | string | Omitted |
| error | string | Omitted |
| disabled | boolean | false |
| variant | default, panel | Provider/preset choice or default |

Default provides grouping without another card. Panel uses shared card border, background, radius, padding, and shadow roles. Children remain normal controls or layout primitives; Fieldset does not choose columns or manage their values.

```tsx
import { Checkbox, Fieldset } from '@paraxe/react';
<Fieldset legend="Notifications" description="Choose your updates." disabled={saving}>
  <Checkbox name="digest" modelValue={digest} onModelValueChange={setDigest}>
    Weekly digest
  </Checkbox>
</Fieldset>
```

```vue
<Fieldset legend="Notifications" description="Choose your updates." :disabled="saving">
  <Checkbox v-model="digest" name="digest">Weekly digest</Checkbox>
</Fieldset>
```

Import Fieldset and Checkbox from @paraxe/vue for the Vue example. Native disabled fieldsets disable descendant controls and exclude them from native form submission. HTML exempts controls inside the first legend, so the legend deliberately accepts text rather than an interactive slot. Keep actions outside the legend.

Error text replaces description text and is announced with role alert. The fieldset references the visible message through aria-describedby and marks an error with aria-invalid. Child inputs do not automatically reference that group message; use FormField for individual control relationships. Explicit IDs must be unique and contain no whitespace. React accepts className/style; Vue inherits attributes.

Try `?preview=form-composition&profile=clean&theme=light` in either playground. Browser review remains part of release acceptance; SSR semantics are not a substitute for native browser/keyboard testing.

The fieldset variant is available in the CLI/preset variant catalogue and both framework providers. An explicit prop takes precedence. In the form preview, choose Preset default in the surface selector to follow recipe-studio variant edits.
