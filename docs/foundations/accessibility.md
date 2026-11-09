# Accessibility

Paraxe supplies semantic elements and ARIA in several implementations, but it cannot supply a page’s labels, text alternatives, focus order, or contrast decisions.

- Give `Image` meaningful `alt` text; it is required by the contract.
- Use `Label for` with the matching form control id when labels are external.
- Keep button, link, dialog, and tooltip content understandable without colour alone.
- Dialog and Drawer close on Escape/backdrop by default and restore focus. Vue traps Tab focus; the React implementations move initial focus and restore it but do not implement a Tab loop.
- Popover triggers are wrapper elements, not automatically accessible buttons; place a semantic button in the trigger.

Component pages limit claims to behaviour present in source.
