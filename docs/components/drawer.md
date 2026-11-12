# Drawer

A controlled modal workspace at the viewport edge, using the same layer/focus contract as Dialog. The audit is **development after registry 0.3.0**. See [overlay surfaces](overlay-surfaces.md) for shared naming, initial focus, built-in close, inert background, scroll and nested-layer rules.

```tsx
<Drawer modelValue={open} onModelValueChange={setOpen} side="right"
  labelledBy="details-title" initialFocus="#details-title">
  <h2 id="details-title" tabIndex={-1}>Project details</h2>
  <p>Read the context before editing.</p>
  <Button onActivate={() => setOpen(false)}>Done</Button>
</Drawer>
```

```vue
<Drawer v-model="open" side="right" labelled-by="details-title"
  initial-focus="#details-title">
  <h2 id="details-title" tabindex="-1">Project details</h2>
  <p>Read the context before editing.</p>
  <Button @activate="open = false">Done</Button>
</Drawer>
```

Import Drawer/Button from the corresponding framework package. side accepts left/right, default right. Drawer now has the same Tab containment, Escape/backdrop options and close naming in both frameworks; React additionally accepts className/style. The full-height edge geometry remains appropriate for a docked drawer, while content, borders, padding, close controls and surfaces follow tokens. Long content scrolls inside the panel.

The drawer does not save data or infer whether a draft is dirty. Keep save/discard decisions in app state; use a nested Dialog for a meaningful confirmation, as in the [core preview](https://tobiwebdeveloper.github.io/paraxe-registry/preview/vue/?preview=overlays&profile=clean&theme=light). Parent and child coordinate focus and scroll ownership through the shared manager. Provide unique IDs and meaningful headings.
