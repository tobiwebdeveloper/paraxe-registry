# AccordionItem

A disclosure item inside [Accordion](accordion.md). Available from `@paraxe/vue` and `@paraxe/react`.

| Prop | Type | Default |
| --- | --- | --- |
| id | string | required, unique within its group |
| disabled | boolean | false |
| indicator | boolean | true |
| headingLevel | h2, h3, h4, h5, h6 | h3 |

Supply trigger content through the named `trigger` slot in Vue or the `trigger` React prop. Children form the answer panel. Trigger content must be non-interactive phrasing content because it sits inside a button. The shared indicator is decorative and follows expansion state. Use `indicator=false` only when the replacement still communicates the control's purpose.

Headings wrap real buttons. Instance-scoped IDs connect triggers to panels, and the `hidden` attribute removes collapsed content from interaction. Keep heading levels consistent with the page hierarchy. Item IDs are state keys; DOM IDs are an internal implementation detail.
