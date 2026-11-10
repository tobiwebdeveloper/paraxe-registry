# FormField

A labelled field with a description or announced error. Import FormField (also exported as Field) from @paraxe/vue or @paraxe/react. It keeps value, validation, and native control ownership in the application.

Shared props: id, label, description, error, required, optional, disabled. Explicit IDs are preserved. Development source now generates a stable fallback ID and exposes bindable control props; this is newer than the published framework packages.

```tsx
import { FormField, Input } from '@paraxe/react';
<FormField label="Contact email" description="For project enquiries."
  required error={emailError} disabled={saving}>
  {control => <Input {...control} name="email" type="email"
    modelValue={email} onModelValueChange={setEmail} />}
</FormField>
```

```vue
<FormField label="Contact email" description="For project enquiries."
  required :error="emailError" :disabled="saving" v-slot="{ control }">
  <Input v-bind="control" name="email" type="email" v-model="email" />
</FormField>
```

Import both components from @paraxe/vue for the Vue example. The React child function and Vue scoped slot provide control: id, describedBy, invalid, required, and disabled. Bind them to the actual Paraxe control. A compound InputGroup can sit around that control without changing the relationship. Wrapper labels and visual state cannot replace native control props.

Descriptions appear at `<id>-description`. A nonempty error replaces the description, appears at `<id>-error`, and is announced with role alert. The binding references only the currently visible message. IDs must be nonempty and contain no whitespace. Generated IDs remain stable through updates.

Existing static children/default slots still work with explicit IDs and manually supplied describedBy/invalid attributes. The component never clones children or silently overrides them. Consumers using native HTML inputs must map describedBy to aria-describedby and invalid to aria-invalid themselves; the bindable object follows Paraxe contracts.

The pure core helper formFieldState(props, fallbackId) returns control, descriptionId, and errorId without changing input props. Framework components generate the fallback ID. The helper does not validate entered values.

Use [Fieldset](fieldset.md) to group related controls and [InputGroup](input-group.md) for adornments/actions. The form-composition preview demonstrates both patterns, failure/retry, and native FormData inspection. Browser review remains part of release acceptance.
