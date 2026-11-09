# ProductPage01: application-owned purchasing

This is the next development slice from [Product direction](../product-direction.md): deepen the existing commerce journey before introducing more disconnected layouts. It is development source for a future registry release; the immutable published registry 0.1.2 bundles are not replaced.

## Core audit

ChoiceGroup/Choice already provide labelled selection, disabled choices, and explicit single-selection state. QuantityInput already handles bounded integer quantities and invalid editing drafts. Button already supports native form submission and pending/disabled treatment. Flex, Price and ProductMedia supply the existing layout and visual roles. No new composite or duplicate control is needed for this step.

## Purchase mode

Pass `addToCart(selection)` to enable size selection, quantity, and an Add to cart action inside the existing ProductPage01 layout. Without that callback, the original read-only availability rows and sample notice remain.

```vue
<ProductPage01 :product="product" :add-to-cart="addToCart" />
```

```tsx
<ProductPage01 product={product} addToCart={addToCart} />
```

The callback receives `ProductPage01Purchase`: `{ product, variant, quantity }`. Product and variant are copies, including the product's variant rows, so later inventory prop changes cannot mutate the submitted snapshot. Optional `id` fields are available on product and variant data; supply a stable product ID in real applications. Product name is the compatibility fallback for selection identity.

The application owns catalogue loading, cart state, persistence, network requests and checkout. Its callback should resolve only when an add is accepted and reject on failure. Map stable IDs to your cart API and validate inventory, quantity and price on the server. The UI snapshot is not an authoritative order or a trusted pricing source. Timeout and cancellation policy belong to the app-owned request.

## Behaviour

- No size is preselected. Unavailable sizes are disabled and have an accessible stock label.
- Quantity starts at one and remains disabled until an available size is chosen. Choosing a different size resets quantity; decreasing stock caps the current quantity.
- Submission rechecks selection and positive safe-integer quantity against the latest rendered availability. Empty inventory cannot submit.
- A pending request disables size/quantity controls and blocks duplicate submissions. Success has a status message; rejection preserves the selection and displays a generic alert without exposing backend error text.
- Changing product identity clears size/quantity and suppresses an old request's status on the new product. Inventory updates for the same product preserve a valid selection.

`purchaseLabels` accepts overrides for `chooseSize`, `quantity`, `add`, `pending`, `added`, and `failure`. Existing `outOfStockLabel`, `inStockLabel`, and `availabilityHeading` still apply. `notice` can show app-owned helper text; pass an empty string to suppress it. The default unavailable-ordering notice only appears in read-only mode.

## Connected preview

Choose **product-purchase** in either playground's Recipe studio, or open `?preview=product-purchase`. The demo app owns an in-memory cart, merges quantities by size, updates remaining inventory and the navbar count, and provides a clear-cart action. The cart link targets its preview summary. Reloading clears the demo. It performs no network purchase or checkout.

The demo is a wiring example, not a new Cart01 registry layout. A dedicated cart/order-summary composition remains the next design discussion. All purchase controls inherit shared component tokens and recipes; block CSS only adds token-derived spacing and alignment.

## Validation and release boundary

Both frameworks have SSR checks for callback-gated purchasing, empty inventory and unchanged read-only behaviour. Shared tests cover invalid selections and snapshot isolation. Vue component-renderer tests exercise asynchronous success/failure, duplicate submission, quantity caps, sold-out updates and stale product requests. Framework typechecks and preview builds cover the connected demo. Visual browser review remains pending.

No npm package API changes are required by this slice. Prepare a new versioned registry release after review rather than mutating an existing release's bundles.
