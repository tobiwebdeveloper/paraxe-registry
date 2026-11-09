# Portal01

An experimental member-home layout in Vue and React. It is a new registry block, with workspace navigation, a featured learning path, member metrics, a searchable resource library, and a schedule/activity rail.

## Layout purpose

The sidebar establishes the member's workspace and identity. The main column leads with a clear welcome and one featured learning path, then separates activity metrics from the resource library. A narrower rail groups upcoming sessions and recent activity. Typography-led resource covers distinguish formats without requiring stock photography.

At smaller widths, the rail moves below the library, navigation becomes a compact horizontal group, metrics and resource cards stack, and the decorative learning-path poster is omitted. Flex owns the composition. Card, Badge, Input, Select, Button, Heading, Text, and Progress remain core components.

## Replaceable data and actions

`organization`, `memberName`, `memberRole`, `title`, `description`, and `notice` replace the identity and introductory copy. Pass `resources`, `spotlight`, `events`, `activity`, and `metrics` for your application data. Pass `spotlight=null` to omit the featured path and empty arrays for empty sections.

Resources have unique IDs, format, title, description, metadata, optional saved status, and optional `href`. An actual destination turns a resource title into a link. Sample resources have no destination and do not pretend to open content. Spotlight continuation and event destinations are likewise supplied by the app. Workspace navigation targets real sections within the block.

Search, format selection, and the saved view compose locally. Clearing filters recovers the full library. Saved status, lesson progress, metrics, events, permissions, authentication, and resource access remain application-owned; this layout supplies no gated-access backend.

## Core improvement

Progress now accepts an accessible `label` in both frameworks. Determinate visual and announced values use one bounded state helper; invalid finite/max configurations are rejected. The portal names its learning-path progress explicitly. This change requires the next core/framework releases.

## Recipes and presets

All interface surfaces, accent colours, text, radius, spacing, borders, and focus styles use existing tokens. Local `--portal01-sidebar-width`, `--portal01-rail-width`, and `--portal01-gap` aliases expose composition proportions. The Swiss recipe offers a typography-led treatment; Educational and Clean offer different component flavours without changing the layout or locking the brand.

Open `?preview=portal-01`, or `?preview=portal-01&profile=swiss` to apply Swiss's optional suggested defaults. Recipe studio keeps all axes editable. This is development source, not part of the immutable public registry 0.1.2 bundles.

## Verification

Both framework rendering tests cover the hierarchy, supplied content, real destinations, empty sections, and accessible progress. Data and Vue client tests cover combined search/format/saved filters and recovery. Token checks and production builds cover the registered source. Browser connection was unavailable, so visual, mobile, keyboard, and screen-reader review remains pending.
