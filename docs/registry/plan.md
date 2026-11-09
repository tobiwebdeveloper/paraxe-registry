# Registry foundation and rollout

Blocks live in `registry/`, not in the component packages. A block composes public components into a complete interface and owns its content, responsive layout, data wiring, and local recipe styles. The library owns controls and visual primitives. Playgrounds import the canonical registry source as a preview; they are not a second source of block implementations.

## Implemented foundation

The previously empty `registry/registry.json` now declares a versioned local catalog (`schemaVersion: 1`). Each block records its slug, title, description, category, experimental/stable status, public component dependencies, and Vue/React entries. Each framework declares package dependencies and an explicit source-to-target file map. Assets and shared helpers are part of that map.

`pnpm registry:check` validates metadata, source availability, entry inclusion, unique installation targets, and path containment (including symlinks). `pnpm registry:build` emits framework-specific content bundles and an index under the ignored `registry/dist/`. These development bundles also feed the versioned static release and source-copy installer documented in [Releasing and installing](releasing.md). `pnpm registry:test` checks invalid paths/entries plus the first block's filter logic. Node 22 is used for the TypeScript fixture tests.

The first entry is `kit-room-collection`, an experimental implementation of the supplied collection reference. See [the detailed reference map](kit-room-collection.md).

The catalog now also contains navbar-01, product-page-01, hero-01, and login-01. Their styling follows [preset recipes](../foundations/recipes.md). Registry checks/builds enforce token isolation; whole component skins belong in the core recipe or project override layer, not each block.

## Public alpha priority

Registry 0.1.2 now has versioned static artifacts, a safe source-copy installer in CLI 0.3.0, and a public GitHub Pages gallery. npm archives are prepared for the maintainer to publish. See [release status and instructions](releasing.md). Product families and release priorities are consolidated in [Product direction](../product-direction.md). New recipe and block directions remain a discussion with the user.

## Next stages

1. **Source and preview contract:** keep block files canonical under `registry/blocks/<slug>/{vue,react,shared,assets}`; keep imports relative and component dependencies public. Serve preview assets from the manifest's public targets. Compare isolated light/dark desktop/mobile previews and verify interactions before marking an entry stable.
2. **Schema and automation:** formalize the v1 JSON schema, dependency/version compatibility, required framework parity, license/asset metadata, and CI checks. Reject broken public component imports and stale bundles. Add a preview-asset sync command so manual asset copies cannot drift.
3. **Consumer installation:** add `paraxe list` and `paraxe add <block> --framework vue|react`, with dry-run output, explicit destination, dependency reporting, and overwrite protection. Install only manifest-listed files. Validate paths again at install time; do not run arbitrary registry scripts. Do not silently replace existing project files or its theme.
4. **Distribution:** publish built JSON bundles at versioned URLs, with hashes and a component/CLI compatibility range. A URL must identify an immutable release; local checked-in manifests remain authoritative during development.
5. **Block catalog:** add searchable metadata, preview routes, screenshot review evidence, and examples for product details, galleries, cart, headers, and footers. Promote an entry to stable only when both framework and interaction/visual gates pass.

## Component/block boundary

Use `Flex`, `Grid`, `Tabs`/`Tab`, `Heading`, `Text`, `Button variant="text"`, `Checkbox`, `ChoiceGroup`/`Choice`, `Input`, `Select`, `Slider`, `Price`, `ProductMedia`, `Badge`, and `Swatch` as parts. Size tiles do not require a separate VariantPicker composite; the existing Choice API supports them. A color swatch is an atom that can sit inside a choice or a product caption. Choice uses toggle-button semantics; use its multiple mode for size filters. Required native radio/form semantics are a different concern and must not be claimed for Choice.

The collection block owns the title row, category/facet state, result counting, search/sort, sidebar, product arrangement, promotional note, and responsive visibility. It can evolve as editable registry code without creating a new library component for every arrangement.

Browser review remains pending because no browser is connected. Build/tests establish source consistency, not a visual or accessibility sign-off.
