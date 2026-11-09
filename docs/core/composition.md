# Composition

Prefer the parent/child pairs that establish context: 
- **Accordion** — Use with `AccordionItem`; each item requires a unique `id` and a named `trigger` slot in Vue or `trigger` prop in React.
- **ChoiceGroup** — Use with `Choice`. The group provides selection state to its child choices.
- **List** — Use with `ListItem`. Selection is enabled only when `selectable` is true.
- **Tabs** — Use with `Tab`. A `Tab` outside `Tabs` throws at runtime.
- **Breadcrumbs** — Use with `Breadcrumb` children.
- **Sidebar** — Use with `SidebarGroup` and `SidebarItem` to build navigation.

Composition is structural: the components do not generate application-level layouts, routing, or data fetching for you.
