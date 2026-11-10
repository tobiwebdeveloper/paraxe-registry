# Paraxe product direction and coverage

Paraxe is a composable UI system for building polished websites and software products. Its core components, independent preset axes, visual recipes, and editable registry layouts should compose across product uses. A new product family must not create a separate design system or bypass the tokens.

The current emphasis is **depth in commonly used application components and forms**, rather than adding more recipes. Strengthen shells, navigation, tables, editors, settings, and useful product workflows; demonstrate how the pieces fit together. Organic is retained with a more distinct treatment, while further recipe expansion is paused.

## Application blocks after registry 0.2.0

The agreed sequence is Settings01, Orders01, Course01, and Dashboard01, using the existing Clean, Swiss, and Educational recipes. Each must be a complete, useful layout; connected examples remain separate from numbered blocks.

[Settings01](registry/settings-01.md) is implemented in development: account/profile rail, grouped profile fields, configurable locale choices, notifications, provider-owned security status, and a persistent save/discard bar. Its controlled form/controller covers validation, pending work, failed-save recovery, and restoring the last saved baseline. Core Switch gained native form/label/description and invalid-state support rather than introducing a bespoke toggle. It is an In progress preview, not an addition to immutable registry 0.2.0.

[Orders01](registry/orders-01.md) is implemented in development: a searchable order book, fulfilment filters, global sorting before paging, a detailed in-flow order panel, delivery/activity information, and filtered CSV export. Core Pagination now shares bounded page-window logic and aligns Vue/React variants, shape, and navigation labels. The block stays read-only with application-supplied totals and statuses; payments and fulfilment are app integrations.

[Course01](registry/course-01.md) is implemented in development: an Educational course overview with searchable curriculum disclosures, app-supplied lesson states, a progress/continue-learning rail, educator, and real replaceable study resource. The application owns lesson navigation, completion, and access. Core Avatar now has consistent Vue/React image/size/shape/status behaviour and source-error recovery. The sample lesson/completion flow is preview application code, not an additional numbered block.

Next: Dashboard01 for a cohesive operational overview. Evaluate core gaps before adding local exceptions or another recipe. Settings01, Orders01, and Course01 remain development after immutable registry 0.2.0.

## Published package update — 9 November 2026

| Package | Published version |
| --- | --- |
| @paraxe/core | 1.5.0 |
| @paraxe/design | 1.9.0 |
| @paraxe/vue | 1.4.0 |
| @paraxe/react | 0.3.0 |
| @paraxe/cli | 0.4.0 |

This coordinated update includes nine recipes (including the differentiated Organic), the Nocturne palette, ProductGallery and media improvements, AppShell/navigation/table/form improvements, and CLI schema 2 binary-asset support. Registry **0.2.0** contains eighteen editable blocks in Vue and React; composition examples remain examples. The previous npm versions and immutable registry 0.1.2 stay available.

Run the following in a **PowerShell terminal**. The first command checks the prepared archives without publishing. The second publishes those same archives to npm through pnpm:

```powershell
Set-Location "C:\Users\tobio\paraxe"
& .\releases\npm\publish.ps1 -DryRun
& .\releases\npm\publish.ps1
```

Run the script file itself, rather than pasting its contents. If npm asks for authentication, run `pnpm login` and complete any two-factor prompt in your terminal. The helper verifies the consumer-check record and archive hashes before publication, skips an already-published version only when its contents match, and stops on failure so the same command can be retried.

All five npm versions were published by the maintainer and verified against the exact prepared archives. CLI 0.4.0 pins registry 0.2.0. The command above can be rerun safely: matching published archives are skipped. Future source changes require new versions and new archive verification; do not rebuild changed contents under these published versions. See [publishing commands](registry/publishing-commands.md) and [release details](registry/releasing.md).

Validation passed: all five archive installations, all thirty-six copied bundles and hashes, nine recipe CSS exports, Vue and React production builds, consumer declarations, workspace typechecks, package/registry tests, and the PowerShell dry run. The previous registry 0.1.2 hashes are unchanged. Browser visual review remains pending; blocks stay experimental.

This translates the user's product-use brief into a coverage map and priorities. It is a planning document, not a claim that complete products or backend capabilities already ship.

## Separate three decisions

| Decision | Examples | Where it belongs |
| --- | --- | --- |
| What the product does | Shop, portfolio, learning platform, client portal, publication, internal workflow | Product requirements and block composition |
| How it is delivered | Static/pre-rendered pages, server-driven dynamic pages, SPA navigation, optional PWA features | Application architecture and framework integration |
| How it looks | Default, Editorial, Educational, Clean; proposed Swiss and Brutalist | Recipes, suggested defaults, tokens, and deliberate layout choices |

These decisions overlap. Static hosting can serve interactive client-side applications. A portal can be an SPA and gain PWA capabilities. An enterprise product may contain a CMS or a shop. Do not treat the user's categories as mutually exclusive products or create one recipe per architecture.

## Translate the supplied categories

| Supplied category | Useful Paraxe interface coverage | Application-owned work |
| --- | --- | --- |
| Static web applications | Portfolios, landing pages, documentation, case studies, service pages | Content source, rendering/build approach, hosting, routing, SEO configuration |
| Dynamic web applications | Search/results, feeds, dashboards, account screens, loading/error/empty states | Backend logic, APIs, persistence, server rendering and cache policy |
| Single-page applications | App shells, navigation, forms, dialogs, data views, persistent interaction state | Router, data fetching, state ownership, route focus handling |
| Progressive web applications | Offline and reconnect notices, retry/sync states, install/update prompts when supported | Manifest, service worker, offline storage, platform support, push delivery |
| Ecommerce web applications | Collection, product detail, cart, order summary, purchase and order-status interfaces | Catalogue, inventory, checkout, payments, tax, fulfilment, transaction reliability |
| Portal web applications | Member home, account navigation, resource library, settings, invitations, visible access states | Authentication, authorization, memberships, access enforcement |
| Content management systems | Content list, editor form, media picker, draft/review/publish states, article views | Content schema, storage, publishing workflow, rich-text engine, permissions |
| Enterprise web applications | Dense tables, filters, bulk actions, workflow detail, audit/activity views, approval states | Scale, integrations, security policy, tenant boundaries, audit guarantees, governance |

UI components do not supply payment security, authorization, offline execution, publishing infrastructure, or enterprise compliance merely by rendering those screens. Keep integration boundaries explicit and preserve useful pending, failure, unavailable, and recovery states.

## Product families to organize around

Use these as discovery tags for future examples and registry browsing. Existing registry categories remain unchanged until a deliberate metadata migration is needed.

| Product family | Current building material | Important gaps to evaluate |
| --- | --- | --- |
| Brand and marketing websites | Navbar01, Hero01, FAQ01, Footer01, Pricing01 | Service/feature sections, social proof, contact flow, complete page examples |
| Portfolios and publications | Typography/media primitives, hero, navigation, footer | Case-study narrative, project index, article layout, contents/navigation |
| Commerce | Collection, ProductPage01, Price, ProductMedia, ProductCard, choices and quantity controls | Purchase-ready product flow, cart and order summary, order states |
| Learning and conversational tools | Educational recipe, Chat01, pricing, form/disclosure primitives | Study resources, exercises, progress journeys, application-owned streaming |
| Portals and memberships | Login01 callback boundary, app shell/navigation, forms and data primitives | Member dashboard, resource library, profile/settings, access and invite states |
| Content operations and team workflows | App shell, Table, List, pagination, forms, feedback and overlays | Content workflow, detail panel, bulk actions, approval and audit interfaces |

Current registry entries are experimental layouts. Public component availability is not proof that a complete product family or every interaction already meets release quality.

## Recipes combine with these families

Educational describes a friendly learning treatment, but it can also serve onboarding or a community product. Editorial and Clean can serve shops, publishers, professional services, or portals. Tokens preserve each brand's colours and typography choices.

Swiss is now a development recipe for information-rich websites and workspaces, demonstrated on Portal01. Brutalist is now a development recipe demonstrated on Event01 for an event/creative-launch context. Use the endorsed layout-and-recipe method for further work. Each numbered block must have a useful, distinct composition rather than simply replacing copy or adding decoration.

Examples of combinations:

- A portfolio with a Swiss recipe and pre-rendered project pages.
- A learning portal with the Educational recipe, SPA navigation, and optional offline study features owned by the app.
- A shop with Clean or Editorial treatment, pre-rendered product pages, and dynamic cart/checkout integration.
- A content workspace with restrained styling, authenticated navigation, and app-owned publishing permissions.

## Next milestone: public alpha

Distribution takes priority over adding more recipes or speculative layouts.

1. **Release core packages and CLI together.** Audit published exports, built CSS/recipes, framework compatibility, and a clean consumer install. Keep package versions and registry compatibility explicit.
2. **Publish registry release artifacts.** Build the existing JSON catalogue and framework source bundles. Add a formal schema, immutable release path, integrity hashes, license/asset metadata, and compatible package ranges. These files can be served statically alongside the docs; no catalogue database is required for this stage.
3. **Provide consumer installation.** Implement `paraxe list` and `paraxe add <block> --framework vue|react`, including a dry run, target-path validation, dependency reporting, and overwrite protection. Those commands are implemented in prepared CLI 0.3.0; registry 0.1.2 is now hosted independently on GitHub Pages.
4. **Provide a public gallery.** Make recipes, editable axes, block previews, install instructions, and experimental status discoverable. Keep the development playground separate from a deliberate public documentation experience.
5. **Validate the alpha in real consumer projects.** Verify both frameworks, asset paths, token imports, light/dark modes, keyboard interactions, mobile layouts, and visual review. Build/test success alone is not visual approval. Registry hosting is live; npm publication remains with the maintainer. See [release instructions](registry/releasing.md).

After the alpha, deepen existing product journeys before expanding the list: for example collection to product to cart, or conversation to study resource to progress. Then jointly choose a new family and layout. A useful product journey is stronger evidence of Paraxe's capabilities than many disconnected demonstration blocks.

## Expansion gate

For each proposed block, record the target product/job, reference, layout purpose, core gaps, framework parity, editable content and tokens, integration boundary, and important states. Audit and improve the core first when a shared capability is weak. Keep implementation and visual validation status explicit.

Related: [registry rollout](registry/plan.md), [block quality](registry/block-quality.md), [storefront roadmap](storefront-roadmap.md), and [recipes](foundations/recipes.md).

## Active development slice: product to cart

ProductPage01 now has optional app-owned purchasing in development: size selection, stock-aware quantity, asynchronous add-to-cart, and pending/error states. A connected Vue/React playground demo shows cart count and inventory updates. Existing core controls were sufficient; no new composite was introduced. See [Product purchasing](registry/product-purchase.md).

Cart01 now extends this development journey with an editable bag, separate app-owned order summary, availability handling, and empty/error/pending states in both frameworks. See [Cart 01](registry/cart-01.md). It is staged for the next registry release; payment integration remains app-owned. Further product-family and recipe expansions follow the block-and-recipe formula.

ProductGallery now adds reusable multi-view product media to this journey. It extends core contracts, both frameworks, and shared design tokens. The gallery and ProductPage01 integration are development features for the next coordinated package/registry release. See [ProductGallery](components/product-gallery.md).

The [connected shop demo](registry/shop-journey.md) now composes collection, product, gallery, navbar, and bag around one application-owned state model in both frameworks. This validates the existing commerce slice before introducing another product family or numbered layout.

## Current emphasis: distinct blocks and useful recipe flavours

Composition demos are examples, not additional blocks. The connected shop proves integration but does not count as a new layout. Prioritise standout additions with a defined product purpose, such as Pricing01, the collection, and Portal01, rather than repeatedly extending the same journey.

Portal01 adds a member workspace with a featured path, searchable resources, and schedule/activity rail. Swiss adds another component treatment, with optional suggested defaults and independent preset axes. Continue evaluating block layout and recipe fit together. See [Portal01](registry/portal-01.md) and [recipes](foundations/recipes.md).

[Article01](registry/article-01.md) adds a publication layout: editorial masthead/header, a readable body, contents rail, source/author notes, and related reading. It gives Swiss another product-specific setting while preserving compatibility with other recipes. Core Image loading/failure states were improved first. This is development source for the next coordinated release.

[Event01](registry/event-01.md) adds a poster-led event layout with multi-day programme, speaker lineup, and registration boundary. The Brutalist treatment brings a sixth recipe, with optional suggested defaults and independent preset axes. Core media ratio tokens were wired through during the layout audit.

The owner endorsed the recent flavours and especially their typography/button proportions. Preserve that quality using the [block-and-recipe formula](block-and-recipe-formula.md), rather than treating the visual balance as an accidental result.

[Studio01](registry/studio-01.md) adds a service-studio layout with selected work, capabilities, and an app-owned enquiry form. Studio adds a seventh recipe, with considered display typography and spacious controls. The core form audit improved Select semantics, FormField helper targets, and React Text attribute forwarding.

Recipe studio navigation now scales through a shared searchable catalogue, product-family groups, and explicit entry types. See [Recipe studio navigation](playground-navigation.md). Monochrome button/brand foreground feedback is deferred in the [backlog](backlog.md); continue block/recipe development without changing chromatic palettes during that investigation.

## Recruiting and adoption guides

Careers01 adds a distinct recruiting layout using Swiss: a filterable, grouped role board, company principles, and hiring steps. Sample roles remain explicit until real destinations are supplied. Hero01 is contained by default with an optional full-width mode. Both are development changes pending release.

The [guide hub](guides/start-here.md) now covers installation, core usage, source-owned blocks, and AI implementation. Static HTML, Markdown sources, an AI index, and a generated current-contract snapshot make this an ongoing adoption track alongside block development. Published and development APIs must remain clearly separated.

## Film, atmosphere, and a shared video player

[Film01](registry/film-01.md) expands culture and visual-storytelling coverage with a title frame, synopsis, native trailer, production credits, and viewing destinations. Cinematic is an eighth development recipe, pairing expansive regular-weight display type with small, deliberate controls. Nocturne is an independent dark-plum/light-porcelain base palette; it is not a recipe-owned skin. Explicit preset choices still win.

The core audit replaced React Video's placeholder and extended both framework players with captions, preload, missing/failure states, and rejected-play recovery. Geometry and play controls consume shared tokens. Media hosting and viewing access stay application-owned. All these additions remain development features pending coordinated release.

## Hospitality and binary assets

[Stay01](registry/stay-01.md) adds a guesthouse planning layout with an original generated landscape, date preferences, room-plan comparison, and considered house details. Organic is retained and differentiated from Studio through firmer type, field-note labels, and component-scoped ink/outline action roles. The composition follows the style-specific character endorsed after Film01's revision.

The core Input audit added native min/max/step forwarding in both frameworks. The owner approved [registry schema 2](registry/binary-assets.md): explicit text/base64 encoding, decoded-byte hashes, bounded downloads, and backward-compatible reading of schema 1. The actual Stay01 image and all eighteen legacy release bundles pass consumer copying tests. Current npm and registry 0.1.2 remain unchanged until coordinated release.

## Common application foundations

[ContentEditor01 and the content workspace](registry/content-editor-01.md) deepen everyday app coverage without another recipe. The new block is the controlled writing-form layout; the connected workspace is an example. Core improvements address React AppShell parity, navigation variants/actions, native table controls and selection, and consistent field validation. The next slices should prioritize reusable settings/account forms, data workflows, and product-management forms against this foundation. Real persistence and permissions remain application-owned.
