# MenuItem

An existing Menu child with audited Vue/React parity in development after 0.3.0. It renders a button for an action or an anchor when href is supplied. Use it inside Menu, commonly opened by Dropdown. Current published React 0.4.0 does not export it; use matching workspace packages for this audit.

Shared props are id, href, target, rel, textValue, danger, disabled, and shortcut. React accepts children, optional icon, onActivate, className, and style; Vue uses its default/icon slots and emits activate with the native mouse event. The icon is decorative. textValue supplies a plain accessible label and typeahead text when the visible content needs one. Otherwise letter search reads the label span, excluding the shortcut.

An enabled anchor preserves native navigation. target=_blank gets noopener/noreferrer when rel is omitted. A disabled link has no href; disabled actions/links prevent activation and do not dismiss Dropdown. Disabled entries remain focusable through Menu's keyboard navigation. danger is a semantic visual treatment, not a business operation. shortcut is a decorative caption; an application must implement actual shortcuts separately.

An activation callback can synchronously preventDefault to keep Dropdown open; on an anchor this also cancels navigation. For intercepted router navigation, explicitly close app-owned Dropdown state as appropriate. The component does not await a callback, manage pending operations, persist a change, or confirm an action.

See [Menu](menu.md) for navigation and token roles, and [Dropdown](dropdown.md) for opening, dismissal, focus return, and examples.
