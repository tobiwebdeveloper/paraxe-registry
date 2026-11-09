# Themes and presets

For complete component styling, see [recipes and project overrides](recipes.md). Presets now choose a recipe independently of accent/fonts/radius/density. Load the design baseline, generated preset, generated theme, and project-owned override file in that order; blocks inherit the result.

The package exports themes under `@paraxe/design/themes/*.css` and presets under `@paraxe/design/presets/*.css`. Only `default`, `dark`, and `light` (themes) and `default` (presets) are current — they define the mode mechanics and structural baseline. The other named files (`sand`, `orchid`, `mocha`, `forge`, `electric`, `crimson`, `corporate`, `creative`, `editorial`, `fashion`, `friendly`, `future`, `industrial`, `local-business`, `minimal`, `premium`, `tech`) are **deprecated** in favor of `@paraxe/cli`, which derives a theme and preset from independent atomic fields (base color, accent, chart color, fonts, icon library, radius, density, menu style/accent) instead of bundled named personalities. Run `pnpm paraxe init` instead of importing a named file directly.

Import one theme and one preset after structural tokens. Import order is significant because CSS custom properties cascade.

See `packages/cli/MIGRATION.md` in the repository for the full deprecation rationale and remaining migration tasks.

## Monochrome storefronts

The CLI now supports `monochrome` as an accent. Choose a `neutral` base for a black-and-white surface palette. The brand becomes near-black in light mode and near-white in dark mode, with matching foreground text and neutral shadows. Semantic status colors and chart colors remain independent.

Set `preset.accent` to `monochrome` in `paraxe.config.json` and run `paraxe generate`, or select it during `paraxe init`. Set `data-theme="light"` on the document root for white mode; dark remains the default.

See [Storefront roadmap](../storefront-roadmap.md) for layout tokens, examples, and the path to commerce components and pre-built blocks.

## Radius, density, and card surfaces

Generated presets now connect the radius selection to rectangular component roles and density to layout, control padding, gutters, and section spacing. Regenerate to apply these corrections. Circles and explicit pill variants retain their geometry.

`preset.surfaceTreatment` optionally selects `flat` (default), `bordered`, or `elevated` for default cards, independently of color and density. Explicit Card variants and overlay elevation retain precedence. See the [component appearance audit](component-appearance-audit.md) for findings, migration behavior, and remaining review work.
