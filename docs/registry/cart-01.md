# Cart 01

A responsive shopping bag with product thumbnails, variant details, quantities, removal, availability, and a separate order summary. It uses Flex and existing core controls. Colours, typography, radius, spacing, and surfaces inherit the active tokens and recipe.

## Development previews

Open either playground with `?preview=cart-01` for an interactive sample cart, or `?preview=product-purchase` for the connected product-to-cart demonstration. The standalone cart lets you change quantities, remove items, simulate lost availability, and reset the sample. Checkout remains disconnected. In the connected demo, choose a size, add an item, then scroll to the bag. Quantity edits and removal update the navbar count and remaining product inventory. Reloading resets the demonstration.

This block is registered in the development catalogue for Vue and React. It is **not included in public registry 0.1.2**. It will need a new immutable registry release before public CLI installation; existing releases remain unchanged.

## App-owned data

Pass `lines` and `summary` together. Each line has a unique `id`, `name`, `imageAlt`, positive integer `quantity`, and non-negative `lineAmount`. Optional fields include `variantLabel`, `imageSrc`, `href`, `unitAmount`, `maxQuantity`, and `available`. Images and copy are replaceable.

The summary requires `subtotal` and `total`; `shipping`, `tax`, and `discount` are optional. Amounts are major currency units displayed with `currency` and `locale`. Omitted shipping or tax reads ?At checkout?. The block displays the supplied totals without recomputing charges. Custom lines without a summary never receive sample totals.

## Integration callbacks

- `changeQuantity(lineId, quantity)` requests a bounded positive integer quantity.
- `removeLine(lineId)` requests removal.
- `checkout()` hands control to the application's checkout integration.

Callbacks may be asynchronous. Update app-owned lines and totals before resolving. While a request is pending, mutation and checkout controls lock; failures show a generic recoverable message and do not mutate data locally. Server-side inventory, pricing, authorization, persistence, and payments remain application responsibilities.

Checkout requires non-empty available lines, a summary, an explicit callback, and `canCheckout` (default true). Use `canCheckout=false` while totals are stale. The sample preview cannot create payments or orders.

Stock loss remains visible: an unavailable line displays its actual quantity and a warning, allows removal, and blocks checkout. Empty carts replace the list and summary with the core EmptyState. After removal, focus moves to the nearest remaining control or the cart heading.

## Composition and customisation

Use `as="section"` and `headingLevel="h2"` when embedding the block. Title, eyebrow, links, notice, currency, locale, and the `labels` dictionary are replaceable. Local `--cart01-media-width` and `--cart01-summary-width` aliases control the thumbnail and summary proportions; all other styling consumes shared roles.

Automated coverage includes data validation, Vue/React server rendering, and Vue client interactions. Both playgrounds are typechecked and built. Browser visual and keyboard review remains pending.

The playground Commerce page and public gallery include an **In progress** section. To refresh gallery previews without modifying published bundles, build both playgrounds with `--base=./`, then run `pnpm registry:preview`. Publish the reviewed static gallery with `pnpm registry:deploy`.
