# Popover

A nonmodal interactive surface attached to a real button. The audited trigger, controlled/local state, accessible panel naming, focus/dismissal and nested-stack behaviour are **development after registry 0.3.0**. Read [overlay surfaces](overlay-surfaces.md) for shared props and boundaries.

```tsx
<Popover label="View options" labelledBy="view-title" initialFocus="#view-order"
  trigger={<Button variant="secondary">View options</Button>}>
  {({ close }) => <>
    <h2 id="view-title">View options</h2>
    <label htmlFor="view-order">Sort order</label>
    <select id="view-order"><option>Recent first</option></select>
    <Button onActivate={close}>Done</Button>
  </>}
</Popover>
```

```vue
<Popover label="View options" labelled-by="view-title" initial-focus="#view-order">
  <template #trigger><Button variant="secondary">View options</Button></template>
  <template #default="{ close }">
    <h2 id="view-title">View options</h2>
    <label for="view-order">Sort order</label>
    <select id="view-order"><option>Recent first</option></select>
    <Button @activate="close">Done</Button>
  </template>
</Popover>
```

Import Popover/Button from the matching framework package. Plain child/default-slot content remains supported; the optional render function/slot close helper is convenient for local state. The supplied trigger must be one native button or a component forwarding attributes to its actual button. A default labelled button is rendered if trigger is omitted. Custom triggers keep their own activation handler; prevented activation and disabled controls do not toggle. Forced type=button prevents accidental form submission. aria-haspopup=dialog, expanded and controls are placed on the actual button.

modelValue/onModelValueChange in React or v-model in Vue makes the state app-owned. Omit modelValue for local state; defaultOpen is false. disabled suppresses opening. closeOnOutside and closeOnEscape default true. Outside pointer/focus dismissal preserves the new destination. Escape and explicit close return focus when the panel owned it. A refusal to acknowledge a controlled close request leaves the panel open.

placement accepts top/bottom/left/right, default bottom. Positioning is inline CSS; collision flipping and a portal are not part of this audit. Focus enters the panel but Tab is not trapped. Inside a modal, Tab remains within that modal and can leave the Popover. This is role dialog without aria-modal, not a menu/listbox/tooltip. Use Dropdown with the existing Menu for action menus.
