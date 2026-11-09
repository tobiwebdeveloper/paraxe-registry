# Navbar01, ProductPage01, Hero01, and Login01

These are editable registry blocks, with canonical Vue/React entries and scoped CSS under `registry/blocks/<slug>/`. They compose public Paraxe components; their content, routes, and product/auth wiring do not become library components. All four remain experimental pending visual/browser review.

## Replaceable branding and assets

No reference logo is required. Navbar01 defaults to a neutral Paraxe mark, and garment illustrations use a small P. mark rather than IMI. Every meaningful image can be replaced: Navbar01/Login01 expose `logoSrc`, ProductPage01 accepts `product.imageSrc`/`imageAlt`, and Hero01 accepts `imageSrc`/`imageAlt` or custom media content. SVG fixtures are editable registry assets, not baked into the component library.

Hero01 does not recreate the reference shirt artwork. It uses a neutral P. treatment until media is supplied. The hero's media slot is also the intended future insertion point for an animation adapter.

## Navbar01 — `navbar-01`

| Reference part | System composition |
| --- | --- |
| Thin dark top strip, pale header, lower hairline | Navbar plus scoped theme/border tokens; top strip is configurable. |
| Small crest at the left | Image inside a named home link; replaced by a neutral sample mark. |
| Centered The shop / The collection ↗ / Cart (0) | Native links inside Flex, with configurable destinations/count. |
| Underlined active The shop | Controlled `activeLink` and native aria-current. |
| Small right-aligned edition | Text in inline Flex; Paraxe / 01 defaults. |
| Narrow screen | Links wrap to a second row; no links are hidden behind an unrequested menu. |
| Fullscreen notice in the first reference | Excluded as browser UI. The unobstructed second image determines the navigation. |

Props live in `navbar-01/shared/types.ts`: brandName, logoSrc, shopHref, collectionHref, cartHref, cartCount, activeLink (shop/collection/cart/null), the three link labels, editionLabel, and edition. Default paths are `/shop`, `/collection`, `/cart`; connect actual routes. An arrow is decorative, not an automatic new-window behavior. The block does not implement a cart.

Layout tokens include `--navbar01-max-width`, gutter, height, top-rule, side-width, link-gap, and logo-width/height. The header is static. The missing React Navbar counterpart was added to the library, using the same brand/content/actions regions as Vue.

## ProductPage01 — `product-page-01`

| Reference part | System composition |
| --- | --- |
| Centered 1200px content and underlined back link | Block max-width/gutters and a real navigation anchor with Text. |
| Tall square-cornered grey image area | ProductMedia, ratio 1 / 1.12; replaceable local sample asset. |
| Broad image / narrower details, generous gap | Flex with 1.15:1 weights and an 80px desktop gap. |
| Uppercase development eyebrow | Text with tracked small typography. |
| Large naturally wrapped product title | Real h1, fluid 32–52px typography and tight tracking. |
| £28.00 / sample price | Price plus baseline Flex and muted Text. |
| Paragraph and Sizes & availability heading | Text and h2, with token spacing. |
| XS unavailable; S/M/L/XL each 8 in stock | Semantic dl/dt/dd rows, using Flex and hairline dividers. |
| Preview notice | Replaceable copy; no API setup instructions in the product flow. |
| Mobile | Columns stack at 48rem; all information remains visible. |

`ProductPage01Product` accepts name, amount in major units, currency, locale, description, optional imageSrc, required imageAlt, and variants `{size, stock}`. Sizes must be non-empty/unique; stock must be a non-negative safe integer. Price reuses the core formatter. Missing images have the existing media fallback; no variants shows the configured unavailable label.

Block props include product, backHref/backLabel, eyebrow, priceNote, availabilityHeading, outOfStockLabel, inStockLabel, notice, and `as` (main by default; use section when embedding inside an existing main). The in-stock suffix is customizable; edit the registry stock-row expression for languages needing a different sentence structure. No variant-picker or stock-table component was invented for read-only rows.

Navbar01 is independent; the product-page preview composes it above the body. Neither bundle requires the other. Core React Text/Heading gained recipe className/style support, matching Vue fallthrough styling.

## Hero01 — `hero-01`

| Reference part | System composition |
| --- | --- |
| Split editorial hero with a slightly wider text side | Row Flex with 1.1:1 weights, equal panel heights, zero gap. |
| Tiny dot + tracked eyebrow | Inline Flex and Text. |
| Two large bold lines with tight tracking | Heading with independently editable titleLines. |
| Supporting paragraph | Muted Text with a restrained measure/line-height. |
| Dark rectangular CTA and diagonal arrow | Native link styled with canonical button CSS, containing inline Flex. It stays a navigation link. |
| Small footnote at the bottom of the text side | Text placed with auto margin. |
| Accent-token visual panel with diagonal lines/circle | Scoped decorative CSS, not a copied product image. |
| Top caption and two bottom labels | Text and wrapping Flex. |
| Three small benefits below a divider | Wrapping Flex and Text. |
| Mobile | Panels stack; copy, CTA, media and benefits all remain present. |

Props: eyebrow, titleLines, description, ctaLabel/ctaHref, footnote, mediaEyebrow/mediaCaption/mediaCredit, imageSrc/imageAlt, highlights, and headingLevel (h1/h2/h3). Vue exposes a named media slot; React accepts a media node. Custom content takes precedence over the default image/mark. Use empty alt for decorative media, meaningful alt for informative artwork. Theme hooks include media background/text, copy surface/padding, and minimum height. The visual panel uses the preset accent and its paired foreground; no yellow is hard-coded.

## Login01 — `login-01`

A compact centered form with Paraxe branding, heading/copy, labelled email/password inputs, remember choice, show/hide password, primary submit, and recovery/registration links. It uses Flex, Heading, Text, Image, FormField, Input, Checkbox, and Button. It is a block, not an authentication SDK.

`authenticate` is an optional async callback receiving `{email, password, remember}`. Without it the submit button is disabled and the preview explains sign-in is unavailable. With it, native required/email validation applies, pending state prevents duplicate submission, failures show a generic alert, and successful completion clears the password. The callback owns session creation, server-side validation, redirects, and persistence. The block never logs or stores credentials and never sends a request by itself. Remember me is passed to the callback; it does not silently create browser storage.

Visible copy and destinations are configurable. The labels object overrides email/password/remember, show/hide, submit/pending, forgot-password/sign-up, and incomplete-form strings. Other props cover brandName/logoSrc/homeHref, title/description, recovery/registration paths, and unavailable/failure/success messages. Password visibility is a real button with aria-pressed/aria-controls. Errors have role=alert and are associated with the inputs. IDs are generated per instance.

Core Button now explicitly supports native button/submit/reset types, and Input exposes describedBy/invalid in both frameworks. Login01 now uses the default core Card and follows its surface/radius/density tokens; it does not hard-code an auth provider or third-party brand.

## Previews and verification

Both playgrounds support `?preview=navbar-01`, `?preview=product-page-01`, `?preview=hero-01`, and `?preview=login-01`; previews default to light mode. Product-page includes Navbar01, while other routes isolate their block. All blocks also appear in the component lab.

Registry file maps include their own framework source, shared data/types/CSS, and required public assets. `pnpm registry:build` emits independent bundles. The registry tests compile and server-render the actual Vue/React entries, including custom media/empty stock/disconnected auth states. Model, component, type, and build checks supplement this. Real authentication, native keyboard/form interaction, responsiveness, focus and pixel comparison still require browser review. Entries remain experimental rather than claiming visual sign-off.

See the [animation integration plan](../foundations/animation-integration.md) for the optional SVG/Lottie direction.


## Styling authority

References guide composition, not a frozen skin. Select the compact/editorial/monochrome treatment through [presets and recipes](../foundations/recipes.md). Blocks do not redefine foundation tokens; project-owned CSS can replace complete component treatments after the generated styles.

## ProductPage01 development update

An optional application-owned purchase flow is now available in development source. See [Product purchasing](product-purchase.md) for callback data, state handling, and the connected demo. It retains read-only availability when no handler is supplied.
