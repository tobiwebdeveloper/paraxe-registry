# Dialog

A controlled modal task/decision surface. Shared stack, naming, focus containment/return, inert background, built-in close action and scroll ownership are **development after registry 0.3.0**. See the [shared overlay contract](overlay-surfaces.md) for props, nesting and limitations.

```tsx
const [open, setOpen] = useState(false);
<Button onActivate={() => setOpen(true)}>Edit project</Button>
<Dialog modelValue={open} onModelValueChange={setOpen}
  labelledBy="project-title" initialFocus="#project-name">
  <h2 id="project-title">Edit project</h2>
  <FormField id="project-name" label="Project name">
    {control => <Input {...control} modelValue={name} onModelValueChange={setName} />}
  </FormField>
  <Button onActivate={() => setOpen(false)}>Cancel</Button>
</Dialog>
```

```vue
<Dialog v-model="open" labelled-by="project-title" initial-focus="#project-name">
  <h2 id="project-title">Edit project</h2>
  <FormField id="project-name" label="Project name" v-slot="{ control }">
    <Input v-bind="control" v-model="name" />
  </FormField>
  <Button @activate="open = false">Cancel</Button>
</Dialog>
```

Import Button, Dialog, FormField and Input from the corresponding framework package. Any save operation remains app-owned. IDs must be unique if multiple examples are rendered. Supply closeOnBackdrop/closeOnEscape (both true by default) to control those dismissal requests. An app may keep the controlled modal open until a pending operation finishes; preserve an understandable cancellation/recovery path. Focus callbacks can change on rerender without resetting the active field.

Use Drawer for a larger contextual panel and Popover for a small nonmodal form. A modal is not a substitute for a whole page. See [overlay preview](https://tobiwebdeveloper.github.io/paraxe-registry/preview/vue/?preview=overlays&profile=clean&theme=light).
