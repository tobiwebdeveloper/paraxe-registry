# Presets, recipes, and project overrides

Paraxe needs to support different complete visual treatments without endlessly restyling each block. The system now separates shared values from component recipes and editable application composition.

## The layers

| Layer | Owns | Does not own |
| --- | --- | --- |
| Foundation tokens | Semantic colors, typography roles, spacing, sizes, radius, focus, motion | Page-specific selectors |
| Preset axes | Accent/base/chart colors, fonts, density, radius, surface treatment, component defaults | A fixed shop layout or brand image |
| Component recipe | How components use semantic roles; complete control/card/navigation treatments | Forced brand colors or font families |
| Project override file | App-owned token mappings or complete replacement component rules | Generated output that can be overwritten |
| Registry block | Layout, content, state wiring, and token-derived composition | A competing local palette or component skin |

`recipe` is an independent preset field: `default`, `editorial`, `educational`, `clean`, `swiss`, `brutalist`, `studio`, or `cinematic`. It is not the old bundled theme/personality model: choosing editorial does not choose an accent, font, radius, or density for you. The sample recipe gives compact labels, distinct commerce metadata/display roles, quiet secondary controls, and restrained tab/badge treatment. Different component CSS can be supplied in the final override layer. See [release status](../reference/release-status.md) before using development recipes.

## Choose a recipe through the preset

Merge these fields under `preset` in the existing `paraxe.config.json`:

```json
{
  "recipe": "editorial",
  "density": "compact",
  "radius": "none",
  "accent": "monochrome",
  "surfaceTreatment": "flat"
}
```

Then run `pnpm paraxe generate`. These choices can produce the reference's compact monochrome treatment through the core system. Change accent to emerald/violet, fonts, or radius independently; the same blocks follow them. Choosing default keeps the standard treatment. Old configurations omit recipe and normalize to default.

The generator imports the selected `@paraxe/design/recipes/*.css` entry. Four entries ship in the current npm release; the development checkout has eight. Recipes define shared component rules and typography roles, not block-specific selectors. Editorial values belong centrally to this stylesheet, rather than being copied as raw pixels into every block.

## Replace a treatment completely

Generation now creates `paraxe-overrides.css` alongside the preset file, **only if it does not already exist**. Its path is recorded as `overridesOut`; `--overrides-out` selects a different path. Regenerating a preset never replaces this project-owned file. Theme, preset, and override output paths must be distinct.

Import in this order:

```ts
import "@paraxe/design/style.css";
import "./styles/paraxe-preset.css";
import "./styles/paraxe-theme.css";
import "./styles/paraxe-overrides.css"; // project-owned final authority
```

For example, a project can replace the primary-button recipe rather than asking each block to patch its appearance:

```css
/* paraxe-overrides.css */
.btn-primary {
  background: var(--surface-card);
  color: var(--text-primary);
  border: var(--border-width-thin) solid var(--brand-primary);
  box-shadow: none;
  border-radius: var(--button-radius);
}

:root {
  --typography-hero-size: var(--font-size-7xl);
  --typography-product-meta-size: var(--font-size-xs);
}
```

This file can contain whole component rules, additional selectors, or deliberate token remappings. It is not limited to small numeric adjustments. Use ordinary CSS specificity when replacing an existing selector; importing last wins equal-specificity rules. Keep theme-role references for predictable light/dark support. The application owns this layer, so it can deliberately override a preset decision; shipped registry blocks cannot silently do the same.

## Compactness belongs in the core

Density now controls control heights, padding, page gutters, option spacing, and checkbox row rhythm. Base control heights are compact 36px, comfortable 44px, spacious 52px; small/large variants and checkbox targets have their own roles. Choose a density appropriate for the interaction context; compact is intentionally denser than the previous implementation.

Typography now has explicit hero, collection-title, product-title, product-name/price/meta, and micro roles. Large editorial headings and small catalog captions can coexist without reducing paragraph text everywhere. `Price size="detail"` uses the detail-price role. Checkbox decoration and option gaps are core roles, not per-block hacks. Input/Select offer a plain treatment for composed toolbar/search contexts; they retain native semantics and focus behavior.

Card default surface treatment stays independent. Login01 uses the core Card so flat/bordered/elevated, radius, and density work normally. Media corners follow the media-radius role; selecting square photography is a project/preset decision, not a rule frozen inside every block.

Navbar/Tabs defaults can come from generated CSS. React now exposes `ParaxeProvider` for the same explicit/default precedence used by these components in Vue; pass preset variants through the provider for deterministic SSR. Explicit component props still win. Broader React variant parity can build on this hook.

## Registry guardrail and previews

All five registered blocks were audited. Their CSS defines only namespaced block aliases; it cannot replace foundation color/radius/density tokens, freeze literal theme values, or reference missing roles. `pnpm registry:styles` checks this, and registry check/build runs it before emitting bundles. Assets remain replaceable images; their illustration colors are not component-theme overrides.

Hero01's visual panel uses accent and its paired foreground, not yellow. Its CTA uses the component recipe. The collection no longer forces monochrome colors or square control corners locally. To recreate that reference, select those decisions through the preset.

Both playgrounds load the selected recipe, generated axes/theme, and project overrides in order. Add `&recipe=editorial` to an isolated preview URL (for example `?preview=hero-01&recipe=editorial`) to inspect the alternate treatment without modifying the saved preset. A missing query uses the project's saved choice. The final override file loads last in both previews too.

Regression checks cover recipe sharing, protected overrides, multiple accents/modes/radii/densities, and block token isolation. Visual/interaction comparison still requires a connected browser; these checks do not claim pixel-perfect matching.

## Suggested setup defaults

`paraxe init` starts with the recipe and asks whether to use its suggestions. Editorial suggests monochrome, Inter, compact density, square corners, flat surfaces, underline tabs, and a transparent navbar. Default suggests the existing general-purpose configuration. Every subsequent setup choice remains editable.

Suggestions are starting points, not CSS constraints. Generation and changing `preset.recipe` never reapply them to existing projects. To intentionally start from a profile in code:

```ts
import { createRecipePreset, RECIPE_PROFILES } from "@paraxe/cli";
const preset = createRecipePreset("editorial", {
  accent: "emerald",
  radius: "lg",
});
```

Explicit values win; font and component-variant choices merge individually. Profiles are exported as metadata so future setup interfaces can show the same descriptions and suggestions.

## Educational and Clean

| Recipe | Treatment | Suggested setup axes |
| --- | --- | --- |
| Educational | Confident buttons with a pressed edge, bolder study controls, readable disclosure rows, friendly conversation surfaces | Lime accent, Outfit headings, Inter body, lg radius, comfortable density, bordered surfaces |
| Clean | Quiet controls, restrained type, simple disclosure rows, quiet conversation surfaces with accent-tinted user messages | Monochrome, Inter, sm radius, comfortable density, bordered surfaces |

Suggestions are optional. Recipes never force these accents, fonts, corners, density, or card surface choices. All seven recipes are included in setup, sharing, generation, and package CSS exports. [Chat01 and Pricing01](../registry/learning-blocks-01.md) demonstrate the new treatments.

Playground-only `profile=educational` or `profile=clean` previews the suggested axes without writing configuration. `recipe=educational` changes only the treatment and preserves saved axes. A recipe query can also override a preview profile's treatment. `theme=dark` selects the dark preview mode.

## Live recipe studio

Both playgrounds have a collapsible **Recipe studio** above the component playground and every isolated block preview. Change recipe, accent, neutral palette, heading/body/mono fonts, density, radius, card surface, and colour mode in place. Switching recipes keeps the other axes and current component state. Existing variant controls remain available in the Vue component playground.

**Apply suggested defaults** intentionally loads the selected recipe's recommendations; it is separate from switching treatments. **Reset to saved preset** restores the imported project configuration. **Export config JSON** downloads the current configuration with preview edits; it does not write files automatically. Existing project overrides still apply last and may override what a control sets.

The URL stores the preview preset for sharing. Use the studio's Preview selector to switch between blocks without losing the experiment. Light/dark selection also survives those navigations. Invalid encoded preset URLs fall back safely. Browser history replacement keeps slider/select experiments from creating dozens of Back-button entries.

This is playground tooling, not part of the registry blocks or public component library. Future recipe and block design directions remain a joint discussion before structural changes.

Run `pnpm playground:test` for the preview-state regression checks.

## Swiss (development)

Swiss is an information-design treatment for publication sites, professional services, research, and structured member workspaces. It emphasizes assertive heading hierarchy, measured whitespace, consistent rules, and typographic controls. It does not turn an arbitrary layout into a Swiss composition; layout quality still belongs to the block.

The optional suggested profile uses Inter, a red accent, square corners, comfortable density, bordered surfaces, and underline tabs. These are setup suggestions, not constraints. Selecting the recipe alone preserves the project's fonts, palette, density, radius, surfaces, and variants. Apply suggestions explicitly in Recipe studio, then customise any axis.

The treatment lives in `@paraxe/design/recipes/swiss.css`; CLI generation imports it for `recipe="swiss"`. Both playgrounds include it in live preview and shared preset URLs. Test it with Portal01 via `?preview=portal-01&profile=swiss`, or change only treatment via `?preview=portal-01&recipe=swiss`. Swiss is staged for the next coordinated design/CLI release.

## Brutalist (development)

Brutalist gives events, creative launches, and independent studio websites a more emphatic component treatment: oversized headings, stronger control borders, direct labels, and hard-offset button shadows. It keeps card surfaces, radius, fonts, brand, and density owned by the preset. It does not automatically turn any layout into an event poster.

Its optional profile suggests a yellow accent, Space Grotesk headings, Inter body text, square corners, comfortable density, bordered surfaces, and enclosed tabs. Selecting the recipe alone does not apply those suggestions. Explicit choices win and survive sharing. Apply the profile deliberately, then adjust any axis.

The treatment ships as `@paraxe/design/recipes/brutalist.css` in development builds and is listed by the CLI and both Recipe studios. Try `?preview=event-01&profile=brutalist` for the suggested profile, or `?preview=event-01&recipe=brutalist` to preserve the project's other axes.

| Treatment | Useful starting point |
| --- | --- |
| Default | Versatile application and website foundations |
| Editorial | Shops, journals, and compact product detail |
| Educational | Study, onboarding, and guided member experiences |
| Clean | Product websites, pricing, and restrained interfaces |
| Swiss | Publications, research, and information-rich workspaces |
| Brutalist | Events, creative launches, and emphatic public-facing pages |

These are starting points rather than product restrictions. Layout and recipe should be evaluated together. All seven treatments remain experimental and require visual review for the actual content and selected palette.

## Studio (development)

Studio is a type-led treatment for independent practices, portfolios, and professional service websites. Display headings use lighter weight and a clear scale relationship to readable body text and compact action labels. Labels are sentence case; secondary controls and rules stay restrained.

The optional profile suggests Fraunces display type, DM Sans body type, stone neutrals, a teal accent, spacious density, larger corners, and flat card surfaces. Explicit choices override these suggestions. Switching to the recipe alone preserves all preset axes and variants.

The treatment ships as `@paraxe/design/recipes/studio.css` in development builds. CLI setup, generation, sharing, and both Recipe studios include it. Try `?preview=studio-01&profile=studio`, then adjust the independent axes. The [formula document](../block-and-recipe-formula.md) records the typography/control relationship that guides this work.

## Navigating the growing playground

Recipe studio has Library, Design, and Typography sections. Library searches and groups previews by product use and entry type, preserving your current preset when switching pages. Recipe/axis controls live under Design; font choices live under Typography. See [navigation details](../playground-navigation.md). Monochrome button/foreground treatment is a deferred [backlog item](../backlog.md).
