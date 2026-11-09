# Storefront foundations and block roadmap

Paraxe should support polished shops as well as application interfaces. Build reusable foundations first, commerce components second, and pre-built page sections once those components are stable.

The wider product coverage and public-alpha priorities are tracked in [Product direction](product-direction.md). This document remains the detailed commerce track.

## Reference and direction

The supplied shop CSS demonstrates an announcement strip, editorial split hero, category navigation, filter sidebar, sorting and search, image-led product grid, product details, and promotional footer sections. Preserve its restrained hierarchy, strong typography, fine borders, generous spacing, and square product photography. Its later overrides introduce many one-off pixel values and duplicate rules: extract shared roles rather than copying the entire stylesheet. Yellow artwork is an optional brand treatment, not part of monochrome.

## Level 1: foundations (started)

- [x] Add an adaptive monochrome accent to the existing CLI, preserving independent font, radius, density, menu, and chart choices.
- [x] Use near-white brand ink on dark backgrounds and near-black on light backgrounds; invert button and selection text with the brand.
- [x] Use neutral shadows for monochrome. Keep semantic success/error colors and chart hues meaningful.
- [x] Add configurable catalog/grid/media/price CSS primitives with responsive column counts, media ratio, object fit, gutters, and filter width.
- [x] Audit component radius, density, and card surface treatment; connect missed anchors and record component-local exceptions in the [appearance audit](foundations/component-appearance-audit.md).
- [x] Add independent default-card surface treatment controls (flat, bordered, elevated).
- [ ] Add typography measure/tracking roles and consistent inverse sections.
- [ ] Exercise the foundations in both framework playgrounds and review desktop/mobile screenshots, keyboard focus, contrast, long names, missing images, and reduced motion.

## Level 2: commerce components

Define framework-neutral contracts in core, then matching Vue and React implementations using design tokens. Start with Price (consumer-supplied locale/currency, sale and compare-at values), ProductMedia and ProductCard (link semantics and independent actions), swatch/size selection, QuantityInput, and responsive product gallery. Include unavailable, selected, disabled, loading, error, empty, and long-content states. Avoid nesting action buttons inside product links.

Then compose collection toolbar, filter groups, active filters, result count, pagination, cart line item, cart summary, and cart drawer. Filters must remain accessible on mobile; collapsing a sidebar must not silently remove the only way to filter. Announce cart updates and restore focus after closing overlays.

## Level 3: pre-built blocks

After component contracts and framework parity are reviewed, create composable announcement/header, split hero, collection with filters, product detail, cart drawer, newsletter, trust strip, and footer blocks. Expose slots/content props and scoped tokens rather than copying component CSS. Provide monochrome light/dark examples and one branded example to prove customization.

## Level 4: complete storefront examples

Build collection -> product -> cart examples with realistic fixtures, working search/sort/filter/variant selection, empty states, and responsive layouts. Keep catalog loading, persistence, inventory, tax, checkout, and payment integration in consumer adapters. A UI example must clearly distinguish demo actions from a real order.

## Current implementation and use

In `paraxe init`, choose `monochrome` as the accent and `neutral` as the base. Existing saved configs can set `preset.accent` to `monochrome`, then run `paraxe generate`. Dark is the default; set `data-theme="light"` on the document root for white mode. Existing color accents retain their behavior. Chart color remains independent; monochrome is an interface accent, not a chart palette.

Import structural tokens, default theme, components, and generated theme/preset overrides in the existing documented order. No additional theme filename or bundled personality is required.

```html
<section class="commerce-catalog" aria-label="Collection">
  <aside aria-label="Filter products"><!-- labelled filter controls --></aside>
  <div class="commerce-grid">
    <article>
      <a href="/products/linen-shirt">
        <div class="commerce-media"><img src="/shirt.jpg" alt="Natural linen shirt, front view" /></div>
        <h3>Linen shirt</h3>
      </a>
      <p class="commerce-price">£48.00</p>
    </article>
  </div>
</section>
```

Scope customization to a wrapper: `--commerce-columns: 4`, `--commerce-columns-mobile: 2`, `--commerce-image-ratio: 3 / 4`, or `--commerce-image-fit: contain`. Defaults are three/two/one columns at desktop/tablet/mobile; breakpoints are 64rem and 48rem. On mobile filters stack above products and remain visible. Price, ProductMedia, and ProductCard now have Vue/React implementations; pre-built blocks remain planned.

## Completion gates

Each component needs a documented contract, Vue/React parity, keyboard and screen-reader behavior, and light/dark visual review before a block depends on it. Each block needs narrow-screen verification and customization examples without selector overrides. Preserve current application layouts and old saved presets throughout.

## Layout, positioning, density, and icons follow-up

The chart screenshot exposed a playground rule, `.grid-2 { align-items: start }`, which intentionally prevented equal-height cards. It now stretches cards within each row and uses the shared grid gap; its minimum track size is also capped at the available width to avoid narrow-screen overflow. Grid now exposes `align="stretch|start|center|end"` in Vue and React, defaulting to stretch. This equalizes card shells within a row; chart plots and legends retain their own natural sizes. Equal chart plotting areas require a separate chart composition review, not arbitrary fixed card heights.

Density investigation found that the generator previously changed only `--space-4`, while normal card padding and grid gaps used `--space-6`. Generated presets now derive card padding plus grid, stack, and inline gap roles from that density anchor. Regenerate saved presets to adopt this change. Follow up with control heights, section spacing, chart sizing, and touch-target checks; keep text and icons independently sized.

- [x] Fix chart grid row stretching and narrow-screen track overflow.
- [x] Expose Grid item alignment in both frameworks.
- [x] Connect generated card and layout spacing roles to density.
- [ ] Review chart plot/legend balance and card header/body/footer composition across content lengths.
- [x] Add a Flex component with row/column direction, wrap, gap, alignment, and justification, retaining Stack for simple vertical composition.
- [ ] Integrate icons end to end: the preset currently records the library but does not install or wire its components. Define a framework-neutral icon contract, Vue/React adapters or resolver integration, consistent size/stroke/baseline rules, decorative versus labelled semantics, and missing-icon behavior. Verify buttons, inputs, navigation, and commerce controls with each supported library.

## Second foundation pass

Implemented `Flex` in core, Vue, and React, including the Vue auto-import resolver. It supports row/column direction, optional wrapping, cross-axis alignment, distribution, density-aware small/medium/large gaps, and full width. Stack remains the simple vertical default. See [Flex](components/flex.md).

The chart showcase now uses at most two columns to give axes and legends enough space, collapsing to one at 64rem. Sparkline rows use Flex to align labels and wrap at narrow widths. Card shells stretch within each row without forcing the compact sparkline content to fill artificial chart heights.

Fixed the Vue chart color resolver's typed-array destructuring compatibility issue with indexed RGBA reads. This preserves color conversion while allowing the repository's TypeScript target to check it.

Browser review was attempted but no connected browser was available. Desktop/mobile visual review remains a release gate; successful compilation does not establish visual balance or contrast.

## Commerce display components (implemented, visual review pending)

- [x] Shared Price contract and Intl formatting helper with explicit locale/currency, sale comparison, zero-price support, invalid-amount checks, and currency-specific precision.
- [x] Price in Vue/React with localizable current/original labels.
- [x] ProductMedia in Vue/React with loading, missing-image, and failed-image placeholders, and independent aspect-ratio/fit tokens.
- [x] ProductCard in Vue/React with category/badge/availability, natural title wrapping, and action content outside the product link.
- [x] Add both playground examples and server-rendered structure checks; ensure the public core helper and React package import in Node.
- [ ] Review desktop/mobile, light/dark, keyboard focus, image-error recovery, and image-source changes in a browser before blocks depend on these components.
- [x] Size/color choices compose existing ChoiceGroup/Choice with Flex and standalone Swatch; QuantityInput provides bounded editing. No separate VariantPicker composite.
- [ ] Next component batch: product gallery, then collection toolbar/filter composition. Keep inventory and cart state in the app; unavailable products must have consumer-disabled purchase actions.

See [Price](components/price.md), [ProductMedia](components/product-media.md), and [ProductCard](components/product-card.md) for the public contracts and customization roles.

## Components and registry blocks

The user's collection reference establishes the boundary: a complete heading/tabs/filter/search/sort/product arrangement is a registry block. Size tiles, swatches, text buttons, and other controls remain library components. The duplicate VariantPicker composite has been removed; compose existing ChoiceGroup/Choice with Flex instead. Choice uses toggle-button semantics and is suitable for multi-select size filters, not an implicit native radio/form replacement.

Swatch is a standalone atom. Choice now supports auto/full width and small/medium/large sizes; Vue group state follows live disabled/multiple props. Flex supports span/div rendering and inline mode so it can be used inside labels/buttons without invalid nested markup. QuantityInput also uses Flex for its internal row.

The first reference collection lives in the registry, with canonical Vue/React entries, shared fixture/filter logic, local SVG assets, and scoped recipe CSS. Playgrounds import these sources. See the [registry plan](registry/plan.md) and [detail-by-detail reference map](registry/kit-room-collection.md). Registry checks/builds are available; an installer, hosting, and visual sign-off remain future stages.

Additional experimental entries: navbar-01, product-page-01, hero-01, and login-01. Branding and images are replaceable; defaults use neutral Paraxe marks. See the [reference block details](registry/reference-blocks-01.md). Optional SVG/Lottie adapters are planned separately in [animation integration](foundations/animation-integration.md), without adding a player to the base UI packages.


## Preset/recipe architecture

The reference must be achievable through core styling, not repeated block overrides. The system now has independent component recipes (default/editorial), semantic editorial typography and control geometry, coherent density heights, and a protected project-owned style override layer. All block palettes/corners are token-driven and checked before registry builds. See [recipes and overrides](foundations/recipes.md). Future skins should extend this architecture rather than copy values into block CSS.

## Website composition and recipe suggestions

Implemented recipe-first setup with optional editable recommendations; existing saved presets keep their choices. Added Footer01 and FAQ01 to both framework registries and a website composition preview. See [website block details](registry/website-blocks-01.md) and [recipe profiles](foundations/recipes.md). Next focus: cart/order summaries, editorial sections, and app-owned form integration.

## Core-first block quality pass

Reworked Footer01 and FAQ01 after auditing their weak composition. Strengthened the core Accordion and React Heading semantics. Future numbered blocks must justify a distinct layout and pass the [block quality standard](registry/block-quality.md); validation limits remain explicit.

## Learning and product websites

Added Educational and Clean recipes, optional suggested-profile previews, Chat01, and Pricing01 in Vue and React. Core Textarea now supports composer sizing and accessible descriptions; Price supports a display role. See [learning and pricing layouts](registry/learning-blocks-01.md). Next: visual review across recipes and widths, app-owned streaming integration, and further distinct website layouts.

## Product-to-cart development slice

Added optional callback-gated purchasing to ProductPage01 in both frameworks using existing ChoiceGroup, Choice, QuantityInput, Button and Flex. The connected local preview owns a cart and remaining inventory. See [purchase behaviour and integration](registry/product-purchase.md). This source is staged for the next registry release; immutable published bundles remain versioned.

## Product-to-cart development

Cart01 is implemented in the development registry in Vue and React, using core QuantityInput, ProductMedia, Price, Card, EmptyState, and Flex. The connected purchasing demo owns cart state and fixture totals. Public release and browser visual/keyboard validation remain pending. See [Cart 01](registry/cart-01.md).

## Product gallery development

Added core ProductGallery contracts, identity-based selection, Vue/React components, Vue resolver support, and shared token styling. ProductPage01 accepts an optional image list while preserving its single-image API. A gallery preview and purchasing demo exercise full and detail views. Package publication and visual validation remain pending. See [ProductGallery](components/product-gallery.md).

## Collection filtering refinement

Added removable active-filter controls, mobile filter counts, a show-results action, and focus handling to both collection blocks. Existing Button, Flex, Tabs, Input, Select, and choice controls were sufficient; no composite was introduced. The same source appears in both playgrounds and the gallery In progress section. Visual/mobile keyboard validation and public source release remain pending.

## Connected commerce composition

Added a shared app-owned shop adapter and Vue/React journey previews composing collection, product, gallery, navbar and bag. Product links, browser hash navigation, filter preservation, stock updates, quantity/removal, and fixture totals share one state model. This is a demonstration rather than a new registry block or backend. See [connected shop](registry/shop-journey.md).

## Standalone blocks and recipe fit

Portal01 adds a distinct member-home composition: workspace identity/navigation, featured learning path, searchable resource library, metrics, and a schedule/activity rail. The Swiss recipe adds typography-led information design with opt-in suggested defaults. Progress gained accessible naming and consistent bounded ARIA/visual values. Composition demos do not count as new blocks. Both additions are staged for the next coordinated package/registry release; browser visual review remains pending.

## Publication block

Article01 adds a standalone editorial reading composition in both frameworks, with replaceable cover/content and native section navigation. Core Image now handles pending, missing, failed, and changed sources. Swiss can be evaluated on both this publication layout and Portal01. See [Article01](registry/article-01.md); release and visual review remain pending.

## Event layout and Brutalist treatment

Event01 adds a distinct public event page in Vue and React. Programme days, speaker references, pricing and registration destinations are editable; the application owns booking/payment. Brutalist adds stronger typography and tactile controls without fixing preset axes. Core media ratio classes now consume their matching tokens. See [Event01](registry/event-01.md); visual review and coordinated release remain pending.

## Service studio and proportion-led recipe

Studio01 and the Studio recipe expand into service/creative practice websites. Core form accessibility was improved first. The [block-and-recipe formula](block-and-recipe-formula.md) now records the owner-endorsed method and the typography/control proportions to preserve. See [Studio01](registry/studio-01.md); visual review and coordinated release remain pending.

## Library navigation and deferred monochrome audit

Both Recipe studios now separate Library, Design, and Typography. Shared preview metadata covers registered blocks, supports search and product/type filters, and retains preset/theme choices across navigation. Monochrome button/brand foreground feedback is recorded in the [backlog](backlog.md), deferred at the owner's request. See [navigation](playground-navigation.md).
