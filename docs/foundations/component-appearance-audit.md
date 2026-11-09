# Component appearance audit

Source audit: 8 November 2026. Covers the shared design CSS, CLI generation, and Vue/React rendering paths. Browser verification remains pending because no browser is connected. This is a source and build audit, not a completed visual or accessibility review.

## Findings and fixes

| Area | Finding | Change |
| --- | --- | --- |
| Radius | The generator only changed `--radius-md`; default preset buttons remained pills, cards/media used `--radius-lg`, and panels used larger scale entries. | Generated presets now derive the rectangular radius scale and explicitly map button, card, badge, tag, form, navigation link, and media roles to the selected anchor. `none` now removes these corners; `full` gives pill-like rectangular surfaces. |
| Radius exceptions | Radios, switches, avatar circles, slider thumbs, progress tracks, and named pill navigation variants use `--radius-full` for their geometry. | Preserved. A square theme must not turn radios into checkboxes or override an explicitly selected pill variant. Commerce photography retains its independently configurable square default. |
| Form customization | Input/select/textarea CSS read the scale directly instead of the existing `--form-radius` role. | Updated the shared rule to consume `--form-radius`, so scoped form overrides work in both frameworks. |
| Layout density | Normal card/grid spacing used fixed scale entries, missing the density anchor. | Card padding and grid/stack/inline spacing now follow the generated density anchor. Flex uses the same gap roles. |
| Control/page density | Button/form padding, container gutters, and section spacing had separate fixed values. | Generated presets now derive these roles from density too. Text, icons, minimum control heights, and chart dimensions remain independent. |
| Surface treatment | Card variants existed, but projects had no independent default surface setting. | Added optional `surfaceTreatment`: `flat`, `bordered`, or `elevated`, exposed in init, shuffle, saved config normalization, and shareable presets. Only default cards consume it; explicit variants retain their styling. |
| Overlay depth | Dialogs, drawers, popovers, and tooltips use their own elevation. | Preserved so flat cards do not remove necessary overlay separation. |
| Surface utilities | Base/raised/card/elevated/glass utilities already exist. | Preserved as explicit composition choices. A global card default does not erase an explicitly chosen glass treatment. |

## Configuration and precedence

Set these fields under `preset` in `paraxe.config.json`, then run `paraxe generate`:

```json
{
  "radius": "none",
  "density": "compact",
  "surfaceTreatment": "bordered"
}
```

Old configs omit `surfaceTreatment` and normalize to `flat`, preserving the previous default card border/shadow behavior. Invalid surface names also fall back to flat. Radius and density corrections deliberately change previously disconnected components after regeneration; existing generated CSS remains unchanged until regenerated. No changes are required to Vue/React Card props.

`flat` means the existing card fill with no border or shadow. `bordered` adds the theme card border; `elevated` adds a subtle border and medium theme shadow. The setting does not alter semantic state colors or page/surface colors. It uses theme tokens so both modes are supported without duplicate palettes.

For local control, override `--card-radius`, `--form-radius`, `--card-padding`, `--card-default-border`, or `--card-default-shadow` on a wrapper. Put project overrides after generated styles. Explicit Card variants (`outlined`, `elevated`, `interactive`, `selected`) take precedence over the default treatment. Selection/focus states and overlay shadows remain intact.

## Remaining review

- Check all three densities with long labels, multilingual text, narrow screens, and zoom. Existing small controls use 36px minimum heights; this audit does not claim every control meets a 44px touch target.
- Audit component-local raw spacing in navigation, checkbox/radio rows, feedback, file upload, chart legends, and composite headers. These still use scale values directly and are not all density-aware.
- Add semantic roles for inset panel and square avatar geometry if projects need those shapes to follow radius. Intentional circles and explicit pills should remain separate.
- Review full-radius cards and large panels visually; CSS clamps large radii to their box geometry, which may be unsuitable for dense dashboards.
- Review flat/bordered/elevated cards in monochrome light/dark, including focus and selected states. Default treatment is card-scoped; a generic Surface component and configurable overlay treatment remain future work.
- Resolve the independent interaction/disabled-state and contrast audit before treating this as a complete accessibility sign-off.

See the [storefront roadmap](../storefront-roadmap.md) for subsequent commerce components, icon integration, and blocks.


## Recipe-level follow-up

The newer [recipe layer](recipes.md) supersedes the earlier decision to keep control heights fixed at every density. Compact/comfortable/spacious now select coherent heights and option rhythm. Complete component treatments can be replaced in a project-owned override file, and registry blocks are prohibited from pinning foundation values.
