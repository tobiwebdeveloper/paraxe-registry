# Raising the quality floor

The owner approved improving lower-ranked components and blocks after reviewing the current library on 12 November 2026. Preserve the character of Booking01, the collection, Event01 and the strongest recipes. Judge the weaker items against those standards rather than adding new recipes to disguise gaps.

## First batch: implemented in development

- **Icon:** replace text-name placeholders with shared real SVG, custom path adaptation, semantic sizing and correct decorative/named states in Vue and React.
- **Tooltip:** link the real trigger, preserve help descriptions/events, support focus and hover, dismiss on Escape, and clean up lifecycle resources. Inline collision/portal work remains separate.
- **Footer01:** replace its loose composition with an invitation/directory frame, actual SVG direction cues, native lists, adaptive brand signature and legal row. Preserve props and independent presets.

These changes are after registry 0.3.0 and require another coordinated package release. Previews do not overwrite published bundles. Browser visual review remains pending when the browser connection is unavailable.

## Second batch: overlay audit implemented in development

Popover now has actual-button semantics, controlled/local ownership, linked panel naming, scoped initial focus, dismissal and focus restoration. Dialog/Drawer share native inert/scroll ownership, Tab containment, nested Escape ordering, logical parent contexts and safe portal cleanup. A shared core preview exercises the public adapters. Tooltip consumes only its first engaged Escape so its surface can close next. [Overlay surfaces](components/overlay-surfaces.md) records the contract and limits. Collision/flipping, shadow-root navigation and native-browser review remain separate work.

## Next icon priority

The owner likes the new symbols and explicitly requested library integration soon. The existing preset `iconLibrary` already offers lucide, tabler, heroicons and phosphor, defaulting to lucide. Today it is metadata: the preset generator instructs users to wire a library separately. Connect this choice to explicit Vue/React runtime adapters and CLI guidance in the next icon pass, with Lucide/Tabler first. Preserve the new semantic names, sizing, labels and custom paths; avoid a hidden network fetch or an eagerly bundled full icon catalogue. The local path set remains a fallback, not a claim that the configured library is already active.

## Remaining sequence

1. **Icon adapters/configuration:** connect the existing iconLibrary choice to actual runtime integration, starting with Lucide and Tabler.
2. **Toast:** lifecycle, dismissal, timer pause and announcements; avoid transient messages as the only recovery route.
3. **FAQ01:** audit accordion constraints first, then improve hierarchy, spacing and supporting navigation.
4. **Dashboard01:** oversized recipe typography, intrinsic metric wrapping, prioritisation and responsive density.
5. **Chart parity:** complete analytical behaviour and readable alternatives rather than copying decoration into React.

Continue working in concrete batches with guides, searchable previews, meaningful tests and a separate visual review record. Lower position is not a reason to add complexity to a simple primitive.
