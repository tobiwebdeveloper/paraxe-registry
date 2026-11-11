# InputGroup

One form surface around one Input and optional leading/trailing content. It is a core component, not a composed search or pricing block. Available in Vue 1.5.0 and React 0.4.0 with core 1.6.0/design 1.10.0.

The shared prop invalid defaults to false and marks the wrapper's visual error border. The actual input still needs its own invalid/describedBy/required/disabled props. InputGroup does not clone children, own values, supply a label, or disable trailing actions automatically.

React accepts leading/trailing nodes, children, className, and style. Vue provides leading/trailing slots and a default slot for the control. Use one direct Paraxe Input initially; Select, Textarea, multiple input fields, and arbitrary nested control wrappers are not part of this first contract.

```tsx
<FormField label="Budget in GBP" error={error} required>
  {control => <InputGroup invalid={control.invalid}
    leading={<span aria-hidden="true">£</span>}
    trailing={<span aria-hidden="true">GBP</span>}>
    <Input {...control} type="number" min={0} name="budget"
      modelValue={budget} onModelValueChange={setBudget} />
  </InputGroup>}
</FormField>
```

```vue
<FormField label="Budget in GBP" :error="error" required v-slot="{ control }">
  <InputGroup :invalid="control.invalid">
    <template #leading><span aria-hidden="true">£</span></template>
    <Input v-bind="control" type="number" :min="0" name="budget" v-model="budget" />
    <template #trailing><span aria-hidden="true">GBP</span></template>
  </InputGroup>
</FormField>
```

Import the components from the relevant framework package. Currency is included in the label, allowing its repeated visual symbols to be decorative. Meaningful prefixes or units must also appear in a label or linked description. Adornments are not hidden by default. Interactive trailing content must be a named button with its own disabled state and an intentional type; Button defaults to type button.

The wrapper follows form background, border, radius, height, padding, text, focus, and disabled roles. The form-border-width role lets grouped and ordinary inputs share Educational/Brutalist's stronger borders. Native :disabled includes disabled fieldset inheritance. CSS :has connects direct-input focus/error/disabled state to the surface; focus on an action retains that action's own indicator. Long addon text can wrap within its allotted space rather than forcing the input offscreen.

Use FormField for labels/help/errors and Fieldset for group semantics. Try the [core form composition preview](../core-component-roadmap.md) in either playground with preview=form-composition. This first version targets modern browsers that support :has; visual and keyboard browser review remains pending when a connection is unavailable.
