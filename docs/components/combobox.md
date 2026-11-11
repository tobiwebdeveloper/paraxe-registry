# Combobox

An editable single-select field with local filtering, disabled options, keyboard exploration, optional clearing, and application-owned remote search. Vue and React share the option/search/navigation helpers. This is **development after registry 0.3.0**; the current published Vue 1.5.0 / React 0.4.0 packages do not export it. Use matching workspace core/design/framework packages.

```tsx
import { Combobox, FormField } from '@paraxe/react';
const [assignee, setAssignee] = useState<string | null>(null);
<FormField id="assignee" label="Project assignee" required>
  {control => <Combobox {...control} name="assigneeId"
    options={people} modelValue={assignee}
    onModelValueChange={setAssignee} clearable />}
</FormField>
```

```vue
<script setup lang="ts">
import { ref } from 'vue';
import { Combobox, FormField } from '@paraxe/vue';
const assignee = ref<string | null>(null);
const people = [{ value: 'alex', label: 'Alex Morgan', description: 'Designer' }];
</script>
<template>
  <FormField id="assignee" label="Project assignee" required v-slot="{ control }">
    <Combobox v-bind="control" name="assigneeId" :options="people"
      v-model="assignee" clearable />
  </FormField>
</template>
```

In the React example, people is the same option-array shape as the Vue example. Each option has a unique nonempty string value and visible label, optional description, keywords, and disabled. Duplicate labels are allowed; duplicate/empty values and blank labels are rejected. Empty string is reserved for no selection. Local search folds diacritics/case and matches every query word across the label, description, and keywords. It preserves supplied order. Disabled entries remain visible but cannot be committed.

## Controlled selection and query

modelValue is the controlled selected ID (or null); choosing emits update:modelValue in Vue or calls onModelValueChange in React. There is no internal saved selection. query is a separate optional controlled string, using update:query/onQueryChange; omit it for local search text. Opening starts a fresh empty query. Closing shows the current selected label, without committing the query or a highlighted suggestion. A controlled query must be updated by its owner. Changing the selected ID externally dismisses the popup.

selectedOption preserves a remote selected label when that option is absent from the current results. It is used only when its value matches modelValue. Without either a matching result or selectedOption, the field shows the supplied ID rather than silently clearing application state. Changing options or disabling an existing choice does not erase the stored value; the application reconciles eligibility and validates its submission.

For server search, set filter=false, control query, and supply options/loading/error from the application. Loading or search error hides previous choices and prevents their selection. The application must correlate/cancel requests and discard stale responses; Combobox does not fetch, debounce, or cache. It removes an active reference when the corresponding result disappears. The preview's fictional service demonstrates this ownership, including out-of-order responses and retry.

## Keyboard, labels, and forms

The interaction follows the editable-listbox guidance in the [WAI-ARIA Combobox Pattern](https://www.w3.org/WAI/ARIA/apg/patterns/combobox/). Focus stays on the textbox while aria-activedescendant identifies the highlighted option. Arrow Down/Up opens or explores enabled results; Enter commits; Escape dismisses; Tab continues normal focus without committing. Alt plus Down opens without highlighting; Alt plus Up closes. Home/End and text-editing keys retain native editing behaviour. IME composition does not trigger selection. The popup indicator stays outside the Tab order; optional clearing is a separately named keyboard action.

Provide a visible label through FormField or a native label targeting id; label can supply an aria-label for standalone use. describedBy links external help, invalid marks app-owned validation, and required exposes required semantics. Search errors are announced separately and do not mark a valid committed selection aria-invalid. Once mounted, required uses the textbox's custom validity based on the committed ID, not its query. requiredMessage customizes that message. Native constraint validation needs hydration; server validation remains authoritative.

When name is supplied, a hidden field submits modelValue (or an empty string). The visible search input has no name. Disabling the control excludes that hidden field from native form data. No free text, multi-selection, tag creation, or remote authorization is implied. Loading, search error, emptyMessage, loadingMessage, placeholder, and optional clearable provide focused presentation states.

## Styling and limits

The field uses shared form dimensions, caption typography, border/radius, foreground, focus, and disabled roles. The popup uses card surfaces/radius/shadow and brand-muted highlights. No separate recipe or fixed palette is introduced. Long labels/descriptions wrap inside the available width. The popup is anchored inline: ancestors must allow overflow. Portal rendering, collision flipping, virtualization, and nested interactive option content are outside this first version. Use native Select when a short non-searchable list is sufficient.

Try `?preview=combobox&profile=clean&theme=light` in either playground. It is an In progress core preview, not a registry block. Checks cover shared matching/navigation, both framework renders, labels/submitted IDs, Vue keyboard/clear/disabled/loading/error/empty/IME transitions, stale active IDs, and sample-request recovery. Browser optical, touch/native keyboard, and assistive-technology review remain pending when a connection is unavailable.
