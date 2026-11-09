# AppShell

Development AppShell is available in Vue and React. It composes a sidebar, header, and one main landmark, with preset-driven default/inset variants. It does not supply routing, authentication, or persistence.

Vue uses named sidebar/navbar slots and a default content slot. React uses sidebar/navbar props and children. Both accept variant, sidebarId, sidebarOpen, mainId, and mainLabel. Pass a stable mainId for a skip link; the main region becomes programmatically focusable.

On narrow screens, navigation is an **in-flow disclosure**, closed by default. A caller-owned button controls sidebarOpen and provides aria-controls pointing to sidebarId and aria-expanded. The navbar stays before the disclosed navigation and main content. This is not a modal drawer; use a modal component when focus containment and a backdrop are required. Sidebar's label names the navigation landmark.

Sidebar and SidebarItem now honor preset variants in both frameworks. SidebarItem renders an ordinary button for actions without an href, emits activate/onActivate, preserves native links for destinations, and blocks disabled controls. Item variants can inherit from Sidebar or be overridden explicitly. Expanded remains local disclosure state that follows changed expanded props; update:expanded/onExpandedChange reports toggles.

See the [content workspace](../registry/content-editor-01.md) for a complete composition and the [current contract snapshot](../reference/current-contracts.md) for the API. React AppShell is included from 0.3.0; use Vue 1.4.0 and core 1.5.0 for the matching shared navigation contract. Older React 0.2.0 does not contain AppShell.
