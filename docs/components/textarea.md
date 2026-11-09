# Textarea

Controlled multiline input for Vue and React. Import `Textarea` and optionally `FormField` from the framework package.

```vue
<FormField id="message" label="Your message">
  <Textarea id="message" v-model="draft" :rows="3" placeholder="Ask a question" described-by="message-hint" />
</FormField>
```

```tsx
<FormField id="message" label="Your message">
  <Textarea id="message" modelValue={draft} onModelValueChange={setDraft}
    rows={3} placeholder="Ask a question" describedBy="message-hint" />
</FormField>
```

Supply an element with ID `message-hint` when using that description reference.

Shared props: `id`, `name`, `autocomplete`, `modelValue` (default empty), `disabled`, `readonly`, `error`, `success`, `maxlength`, `placeholder`, `rows`, `required`, and `describedBy`. Boolean flags default false. Vue emits `update:modelValue`; React calls `onModelValueChange` from its native change event. Associate a real label using the same ID. Invalid state sets `aria-invalid`; `describedBy` maps to `aria-describedby` for app-owned help or error text. Surface, type, border, radius, and spacing remain token/recipe controlled.
