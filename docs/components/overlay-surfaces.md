# Overlay surfaces

Popover, Dialog and Drawer share a focus/dismissal layer manager in **development after registry 0.3.0**. This replaces their independent document listeners and adds cross-framework parity. Current npm archives retain earlier implementations. Use matching development core, design and framework packages; preview availability is not release availability.

[Vue preview](https://tobiwebdeveloper.github.io/paraxe-registry/preview/vue/?preview=overlays&profile=clean&theme=light) / [React preview](https://tobiwebdeveloper.github.io/paraxe-registry/preview/react/?preview=overlays&profile=clean&theme=light). The preview edits local workspace details, opens a Popover inside a Drawer, and opens a confirmation Dialog above the Drawer. It is a core example, not another block or a connected backend.

## Choose the surface

| Surface | Intended content | Focus and background |
| --- | --- | --- |
| Popover | Small contextual form or supplementary interactive content | Nonmodal; focus enters, Tab may leave, background remains usable. |
| Dialog | Focused task or decision | Modal; background is inert and Tab stays in the dialog. |
| Drawer | Larger contextual task alongside page context | Modal, with the same focus rules as Dialog; left/right viewport edge. |

Use the existing Dropdown/Menu for a menu of actions. Tooltip is short text and does not receive focus. Do not use a nonmodal Popover to impersonate a menu.

## Shared props

- `id`: optional stable, document-unique panel ID. Otherwise generated per instance.
- `labelledBy`: IDs of visible headings naming the surface; preferred for real content. `label` provides an accessible name when no heading reference is supplied. Fallback names are Dialog, Drawer and Details; replace these with meaningful names in a product.
- `describedBy`: optional IDs for a short description. Avoid referencing a long, structured document as one description.
- `initialFocus`: CSS selector resolved **inside the panel**. A heading/static target needs tabindex=-1. Invalid syntax throws before global background/scroll ownership is taken. A missing, disabled or hidden target falls back to the first eligible tabstop, then the panel if empty.
- `returnFocus`: defaults true. Focus returns to a connected, enabled, visible opener when focus belonged to the closing surface. An intentional new destination is preserved. Set false when the owning workflow explicitly manages the next focus target.
- `showClose`: defaults true, rendering a native type=button close control inside the surface. `closeLabel` customizes its accessible label. If hidden, provide a clear app-owned close/cancel action.
- `closeOnEscape`: defaults true. Only the active top layer requests dismissal. Disabling it on the top layer does not cause a lower modal to close.

Names and references belong to the actual role=dialog panel, not an inert wrapper. The close control has a real decorative SVG. React accepts className/style on all three; Vue accepts class/style attributes on their roots.

## Ownership and nested behaviour

Dialog and Drawer are controlled: React uses modelValue/onModelValueChange, Vue uses v-model. They request false through the callback/event; the owner must acknowledge the request. They do not silently change app state. Popover additionally supports local state when modelValue is omitted, with optional defaultOpen.

Each document has a shared layer stack from the installed core instance. Framework context records logical nesting even when modal portals are DOM siblings and child mount effects run first. The active modal isolates background branches with native inert, including body children inserted while open. Root/body overflow and scrollbar compensation are restored after the last modal closes; nested modal closure preserves the lock. Existing inert attributes and inline overflow/padding values are restored.

Tab/Shift+Tab wrap in the active modal. Hidden/inert, disabled-fieldset and negative-tabindex controls are excluded; radio groups contribute their active tabstop. Static initial headings and empty panels are handled explicitly. Closing a child returns to the parent opener; closing the last modal returns to the page opener where still appropriate. Portal removal before framework cleanup is covered. Removing a parent deactivates descendants and requests their closure. Do not keep a child surface mounted independently while discarding its owning workflow.

A composed Menu or Tooltip may consume Escape before its containing surface. The first Escape dismisses an engaged Paraxe hint; a subsequent Escape can dismiss its surface. Application widgets should preventDefault when they own that Escape. Tab within a nonmodal Popover is natural; leaving it requests closure unless closeOnOutside is false. Outside dismissal preserves the pointer/focus destination rather than pulling focus back.

The modal interaction follows the [WAI modal dialog pattern](https://www.w3.org/WAI/ARIA/apg/patterns/dialog-modal/): name the panel, keep focus within it while modal, provide a close action and choose appropriate initial/return focus. Automated helper/renderer tests do not establish browser or screen-reader conformance.

## Styling and boundaries

Surfaces consume card/background, typography, spacing, border, focus and motion roles. `--dialog-width`, `--drawer-width`, `--popover-width`, `--popover-radius`, `--popover-surface`, `--popover-border` and `--overlay-blur` are configurable. Close controls consume form radius and icon-button sizing. The layer manager owns the temporary `--paraxe-overlay-order` value; do not override it to simulate a separate stack.

Dialog and Drawer portal/teleport to the document body and render after client mounting. Project-global presets therefore work; narrowly scoped ancestor-only CSS variables do not automatically follow a body portal. Pass surface class/style or define project roles at the document root. Framework provider context is retained.

Popover remains an inline CSS-positioned surface with bounded width. This batch does **not** add viewport collision flipping or a floating portal. Avoid clipping ancestors or use a modal/visible section where the content needs more room. Light-DOM native controls and Paraxe controls are covered; embedded-document keyboard boundaries, custom shadow-root tab order and coordination with independent third-party modal managers are not established. Native mobile scrolling, focus, screen-reader and visual review remain pending when the connected browser is unavailable.

Persistence, permissions, save confirmation and destructive operations remain app-owned. Body scroll policy should be coordinated with other application-level scroll managers.
