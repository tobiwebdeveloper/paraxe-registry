# Footer01

A closing layout with a framed invitation and numbered navigation directory, followed by an expressive brand signature and quiet legal row. It is a revision of Footer01, not another numbered block. The revised renderer and SVG icons are **development after registry 0.3.0**; the immutable registry retains the earlier layout.

[Vue preview](https://tobiwebdeveloper.github.io/paraxe-registry/preview/vue/?preview=footer-01&profile=editorial&theme=light) / [React preview](https://tobiwebdeveloper.github.io/paraxe-registry/preview/react/?preview=footer-01&profile=editorial&theme=light). The In progress gallery calls it Footer01 update. Existing profile axes remain editable.

## Content and integration

Existing props are preserved: brand, eyebrow, title, description, contactLabel/contactHref, edition, copyright, groups and legalLinks. Each group has title and links; each link has label and href. Replace all sample destinations before using the footer in a product. Contact is a real anchor; there is no invented email capture, availability badge or backend. Clear contactHref to hide the contact action. Empty groups and legalLinks omit their navigation. The invitation then expands naturally.

The numbered directory uses named sections, native lists and anchors. SVG arrows are decorative. Brand is replaceable text. The large signature wraps long names; shorter names give a stronger typographic silhouette. Group titles, links, invitation text and actions accept wrapping. Narrow layouts stack the invitation and directory, then wrap groups into one column.

## Presets and source

The invitation uses brand-primary-muted with text-primary/secondary, while the directory uses the card surface. Contact uses the recipe's secondary-button classes on an anchor. Radius, density, typography, spacing, border and focus remain semantic tokens. `--footer01-invitation-width` and `--footer01-panel-padding` are local composition hooks, not palette overrides. No extra recipe is needed.

Copy renderer, shared types and CSS together when the next registry release includes this revision. Use matching development framework/design/core packages now: current npm Icon still renders text and cannot supply the new SVG treatment. The original published Footer01 bundle remains compatible with its published packages.

Browser visual review is pending; automated checks cover both framework renderers, long/empty content, linked headings, native navigation and token consumption.
