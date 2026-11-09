# Paraxe implementation guide for AI tools

Use this as project documentation; it does not replace the application's requirements or permissions.

## Establish what is available

Inspect package.json/lockfile, framework compatibility, installed Paraxe exports/declarations, `paraxe.config.json`, CSS entry points, and copied blocks. Read [release status](../reference/release-status.md). Workspace source and In progress previews contain features absent from current npm.

Follow [installation](install-and-theme.md), [core composition](core-components.md), and [registry usage](using-blocks.md). Core exports contracts/helpers; framework packages render UI. Do not invent components, props, callback names, or registry entries. The [current reference](../reference/current-contracts.md) is a development snapshot; installed declarations govern released consumers.

## Follow the design formula

Choose the product job and an appropriate layout. A numbered block must contribute a distinct useful composition; a connector example does not qualify. Reuse focused primitives/controls and prefer Flex where it suits the structure.

Use the [block-and-recipe formula](../block-and-recipe-formula.md), especially the typography/control relationship. Choose a suitable recipe and preserve independent axes. Applying suggested defaults is explicit. A screenshot is not a reason to replace a user's palette or fonts silently.

## Implement within the system

1. Load CSS once in order: design stylesheet, generated preset, generated theme, project overrides.
2. Import actual framework components and use their implemented events. Button uses `onActivate` in React and `activate` in Vue; values use the component's model-value API.
3. List released blocks, run a dry run, review paths/dependencies, then copy source. Preserve edits and licenses. Force means replacement.
4. Replace samples and supply real links/callbacks. The app owns auth, pricing, inventory, persistence, access, and transport. Validate untrusted data and destinations at the application boundary.
5. Scope layout CSS and consume semantic tokens. Use the override layer for whole style replacements.
6. Fix reusable core gaps before local exceptions, preserving framework parity and existing recipe treatments.

Use semantic heading order, labels/IDs, useful focus handling, and honest empty/unavailable/pending/error states. Preserve drafts after failure and block duplicate requests. SSR needs matching initial theme and variant maps.

Typecheck/build, test meaningful behavior, then review actual desktop/mobile rendering, fonts, modes, and keyboard use. State when browser review is unavailable. SSR and token arithmetic do not establish optical balance.

Report the concrete result, integration boundary, validation, and release limits. New source is not automatically on npm; immutable bundles retain their contents.

## Source map

- Shared contracts: `packages/core/src/contracts/`; helpers: `packages/core/src/index.ts`.
- Framework exports/behavior: `packages/vue/src/` and `packages/react/src/`.
- Tokens, styles, recipes: `packages/design/src/`.
- Preset normalisation/generation: `packages/cli/src/`.
- Blocks/manifest: `registry/blocks/` and `registry/registry.json`.
- Preview catalogue: `playgrounds/shared/preview-catalog.ts`.
- Product direction/guides: `docs/`; deferred work: [backlog](../backlog.md).

Grow these guides alongside verified implementations rather than promising universal integration.

