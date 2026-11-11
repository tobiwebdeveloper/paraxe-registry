# Menu

Menu already exists in Paraxe. This development pass retains its name and default/flat/outline variants while adding React parity and shared keyboard behaviour. It composes MenuItem and MenuSeparator; Dropdown supplies the opening/dismissal context. The audited behaviour is **development after 0.3.0**, not part of current published Vue 1.5.0 / React 0.4.0. Published React Menu is an earlier nav wrapper; use matching workspace packages for this implementation.

```tsx
import { Dropdown, Menu, MenuItem, MenuSeparator } from '@paraxe/react';
<Dropdown label="Draft actions">
  <Menu label="Draft actions" variant="default" size="md">
    <MenuItem onActivate={() => duplicateDraft()}>Duplicate draft</MenuItem>
    <MenuItem href="/drafts">Open drafts</MenuItem>
    <MenuSeparator />
    <MenuItem disabled>Publish draft</MenuItem>
    <MenuItem danger onActivate={() => archiveDraft()}>Archive draft</MenuItem>
  </Menu>
</Dropdown>
```

Vue uses the same composition with default slots and @activate handlers. Menus are action/command widgets. For ordinary site navigation, use nav/links, Navbar, or Sidebar rather than assigning menu roles to a document's link list. Links inside an action menu retain actual href navigation; actions use buttons.

## Behaviour and naming

The menu renders role=menu, with label or labelledBy and optional id. Dropdown supplies its generated menu ID and trigger relationship. Outside Dropdown, supply a useful accessible label. Each MenuItem is a menuitem; separators are noninteractive. Only one item is in the Tab order after mounting. Arrow Up/Down wraps; Home/End moves to the ends; letter-prefix search uses the visible item label (or textValue), folds case/diacritics, and cycles repeated letters. The prefix buffer expires after 750 ms. Enter/Space activates the current item. Text composition and modified shortcuts are left alone.

This follows the relevant [WAI-ARIA Menu guidance](https://www.w3.org/WAI/ARIA/apg/patterns/menubar/). Disabled items remain keyboard-discoverable and cannot activate. Shortcuts are display captions, not installed key bindings. Dropdown owns Escape, Tab dismissal, and return focus; a standalone Menu has no invoking trigger to restore.

The shared navigator observes item changes, keeps roving tabindex coherent, and disconnects on unmount. Native fieldset-disabled controls are excluded. If a focused item disappears, it can focus the next available item/root while avoiding a different app surface that already owns focus. Browser/native and assistive-technology review remains pending when no review connection is available.

## Styling

variant accepts default, flat, or outline; size accepts sm, md, or lg. The existing menu preset/provider key supplies a default variant, while an explicit prop wins. Card background/border/radius/shadow, form radius, button-size roles, caption typography, spacing, foreground, focus, and semantic danger colour remain token-driven. Labels wrap without colliding with optional shortcut captions. Flat intentionally removes the menu surface; outline uses a stronger border without shadow.

Use MenuItem children and optional passive labels, not arbitrary form fields, nested tabs, or interactive controls within a menu item. Submenus, checked/radio menu items, and a full menubar are outside this first audit. [Dropdown](dropdown.md), [MenuItem](menu-item.md), and [MenuSeparator](menu-separator.md) describe composition and boundaries.

## Native downloads (development after 0.3.0)

MenuItem accepts `download?: string | boolean`, forwarded only to an enabled anchor with href. This preserves native browser download behaviour for real resources; it does not generate file contents. Application01 supplies a local public role-brief text resource. Disabled items omit both href and download. Cross-origin download handling remains subject to browser rules.
