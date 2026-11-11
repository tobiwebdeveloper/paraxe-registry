# Dropdown

Connects a real menu button to the existing Menu composition. It adds local/controlled open state, keyboard entry, dismissal, and appropriate focus return. This audit and React parity are **development after registry 0.3.0**. Current Vue 1.5.0 contains the earlier click-wrapper version; React 0.4.0 does not export Dropdown. Use matching workspace core/design/framework packages.

```tsx
import { Button, Dropdown, Menu, MenuItem } from '@paraxe/react';
<Dropdown placement="bottom-end" trigger={<Button variant="secondary">Draft actions</Button>}>
  <Menu label="Draft actions">
    <MenuItem onActivate={() => duplicateDraft()}>Duplicate draft</MenuItem>
    <MenuItem href="/drafts">Open drafts</MenuItem>
  </Menu>
</Dropdown>
```

```vue
<script setup lang="ts">
import { Button, Dropdown, Menu, MenuItem } from '@paraxe/vue';
</script>
<template>
  <Dropdown placement="bottom-end">
    <template #trigger><Button variant="secondary">Draft actions</Button></template>
    <Menu label="Draft actions">
      <MenuItem @activate="duplicateDraft">Duplicate draft</MenuItem>
      <MenuItem href="/drafts">Open drafts</MenuItem>
    </Menu>
  </Dropdown>
</template>
```

duplicateDraft is an application callback in these examples. Omit trigger/#trigger and use label to get a native default button. A custom trigger must be one button or a component forwarding native button attributes, such as Paraxe Button. Dropdown clones that element with type=button, its ID, menu attributes, and disabled state; it does not create a nested button. Use an accessible label when the button contains only an icon or avatar. Existing Vue visual-only avatar triggers need a Button around the avatar; the core playground now follows this pattern.

Supply one Menu as the default child. Dropdown gives it the generated menu ID and trigger relationship. MenuItem/MenuSeparator remain the existing menu composition; Dropdown is not a new menu surface. id supplies a stable prefix for the owned IDs rather than an unrelated root DOM ID.

## State and dismissal

Omit modelValue for local state. To control it, bind Vue v-model or React modelValue/onModelValueChange. The event requests a state change; a controlled owner must acknowledge it. Do not switch ownership during a mount. disabled closes the interaction and requests a false controlled value. Native disabled/loading custom buttons cannot open it through user activation.

The button's native Enter/Space activation opens the menu; Down/Up can enter at its first/last item. The interaction uses the [WAI-ARIA Menu Button pattern](https://www.w3.org/WAI/ARIA/apg/patterns/menu-button/). The actual button has aria-haspopup, aria-expanded, and an open-state aria-controls relationship. Keyboard handling within Menu is described in its [guide](menu.md).

Escape closes and restores focus. A programmatic controlled close also restores focus when the menu lost focus to the document body; an existing outside focus destination is preserved. Selection normally closes and returns focus to the button, while avoiding a dialog or other app surface that already took focus. Outside pointer/focus movement closes without stealing the destination's focus. Tab remains a native focus move; closure is deferred until that move can occur. Shift+Tab can naturally return to the trigger. Clicking the trigger again toggles it closed. Listeners and deferred closure are cleaned up on unmount.

Calling preventDefault synchronously on a MenuItem activation event prevents automatic dismissal (and cancels native link navigation for a link). The app can then manage the operation and controlled state. Dropdown does not wait for promises, implement business actions, publish content, or persist records. For an app router that intercepts links, manage dismissal explicitly if navigation is prevented.

## Placement and scope

placement accepts bottom-start (default), bottom-end, top-start, or top-end. Alignment uses logical inline sides. Menus inherit preset tokens and the existing menu variant/size; React also accepts className/style and Vue normal fallthrough attributes. Custom triggers keep their own Button variant.

The popup is inline, with token-bounded width. Choose a suitable placement and allow overflow in ancestors. Portals, automatic collision flipping, submenus, modal focus trapping, check/radio items, and arbitrary popover forms are outside this implementation. Use Dialog/Popover for their own appropriate content patterns; ordinary site navigation remains nav/links or Navbar/Sidebar.

Try `?preview=dropdown&profile=clean&theme=light` in either playground. The In progress entry is a core preview, not another numbered block. It demonstrates existing Menu surfaces, sizes, four placements, local draft actions, real guide navigation, controlled state, disabled entries, and intentional keep-open behaviour. Tests cover both framework renders, shared navigation/typeahead, actual-button naming/relationships, selection/cancellation, disabled links, owner acknowledgement, outside/Tab focus, listener cleanup, and focus handoff. Visual/native browser and assistive-technology review remain pending when no review connection is available.
