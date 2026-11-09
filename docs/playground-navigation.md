# Recipe studio navigation

Recipe studio now separates browsing from styling in both Vue and React. It remains an expandable tool above the preview, with the current preview and recipe visible in its summary.

## Library

Search by title, product use, description, tags, or suggested recipe. Filters narrow the list by product use and entry type. Groups keep related work together, and the current preview is marked explicitly.

Blocks, core components, examples, and the component playground have distinct labels. A connected shop is an example, not another numbered block. Suggested recipe names are hints about fit; opening a preview does not apply that profile or replace the current preset.

Opening another preview preserves the encoded preset, colour mode, search, and filters. It clears old block-specific anchors, so a cart or article hash does not carry into another layout. The library stays open during browsing. The URL retains the studio section and filter state; closing the tool preserves its search in the URL without opening it automatically on reload.

Use Clear filters to recover from an empty result. Unknown shared filter values fall back to the default library state.

## Design and Typography

Design contains recipe, accent, neutral palette, radius, density, card surface, and colour mode. Typography contains heading, body, and monospace families. Recipe descriptions remain beside Design controls. Apply suggested defaults, reset, and export stay available in both styling sections.

Changing a recipe alone preserves independent axes. Applying suggestions is explicit. Saved project files are never changed by the preview controls.

## Maintaining the library

`playgrounds/shared/preview-catalog.ts` supplies both frameworks. Each entry records route value, human label, purpose, type, product family, optional registry name, suggested recipe, and search tags. Tests compare registered blocks with catalogue entries to catch missing or duplicate block navigation. Add the actual preview route in the playground App when adding a new block.

Search/group helpers and URL functions are shared. Native section buttons use pressed state; labelled sections stay mounted and inactive sections are hidden. Links use native navigation and the current preview carries aria-current. There is no new component dependency or preview-fetch service.

## Verification

Checks cover registered-block coverage, filtering, grouping, shared URL validation, preset/theme preservation, old-anchor removal, and Vue-rendered library/section interactions. Both frameworks are typechecked and built. Browser visual, mobile, and actual keyboard review remains pending.

The owner's monochrome foreground/button feedback is recorded separately in the [development backlog](backlog.md), deferred while block and recipe development continues.
