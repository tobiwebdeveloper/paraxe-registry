# Checkout01

A dedicated commerce checkout with an editorial introduction, contact/delivery/review stages, a product-media spread, persistent order summary, and an application-owned payment handoff. Editorial is the suggested recipe. Existing palettes, fonts, density, radius, surfaces, and component variants remain independently editable.

The composition gives forms and the selection separate measures: a quiet working column and a larger product-led summary. Delivery options are native radios in a fieldset. Review includes editable contact/address sections and a confirmed total beside the final action. On small screens the columns stack, field pairs become single columns, and in-page links connect details and summary. Headings wrap rather than borrowing narrow fixed columns from the display type.

Try `?preview=checkout-01&profile=editorial&theme=light` in either playground. Included in registry **0.3.0**, with core **1.6.0**, design **1.10.0**, Vue **1.5.0** or React **0.4.0**, and CLI **0.5.0**. Its shared component improvements ship in these packages. Older immutable registry 0.2.0 does not include this layout.

## Use the block

Copy the Vue default Checkout01 entry or named React Checkout01 entry with shared checkout.ts and checkout.css. Create a stable controller in application setup and pass it through controller. Do not create it again on every render. Optional title, description, logoSrc, and backHref customize the page. Brand text, products, imagery, supported countries, and delivery options come from the checkout record. Locale formats money; the current interface copy is English and editable in the copied source. Back destinations accept relative paths or HTTPS.

```ts
import { createCheckoutController } from './blocks/checkout-01/shared/checkout';
const controller = createCheckoutController(checkoutRecord, {
  quote: request => deliveryService.confirmQuote(request),
  continueCheckout: request => paymentApplication.openSession(request),
}, savedDetails);
```

The services above are application adapters, not Paraxe services. React passes controller to `<Checkout01 controller={controller} />`; Vue uses `:controller="controller"`. A server-rendered application must create one controller per request/user, not a module-level shared customer store. Subscribe to getSnapshot for application integrations; snapshots are immutable. The controller owns the in-memory draft and flow, not server persistence.

## Product and delivery data

CheckoutRecord contains id, brand, currency, locale, lines, countries, and deliveries. IDs must be unique alphanumeric identifiers with optional hyphens/underscores. A line contains id, name, detail, quantity, amountMinor, optional imageSrc, and imageAlt. amountMinor is the entire line amount; do not multiply it by quantity again. Quantities and all money amounts must be safe nonnegative integers, with positive quantities. Line records are copied/frozen. The quantity total and subtotal must also be safe integers.

Amounts use the currency's minor unit. GBP 2800 means £28; JPY 2800 means ¥2,800. Currency formatting derives its precision through Intl.NumberFormat. This block deliberately uses explicit Minor suffixes, unlike the existing Cart01 major-unit contract. Convert at the application boundary rather than mixing representations.

Countries contain code, label, optional postalLabel, and optional postalRequired (defaults to true). Deliveries contain id, title, description, amountMinor, and optional disabled. These amounts are delivery estimates shown with the options; the returned quote supplies the confirmed charge. The app owns supported-destination policy, postal/address verification, fulfilment availability, and authoritative pricing.

The copied sample SVG products are replaceable media assets, not fixed UI palette colours. Replace their paths and alt text for a product. The media spread is omitted when no image sources are supplied. Empty lines produce a separate empty-bag state.

## Quotes and state ownership

Create the controller with quote(request), optional continueCheckout(request), and optional now() for deterministic testing. An optional partial CheckoutValue prefills the draft. Fields include email, firstName, lastName, address1, address2, city, region, postalCode, country, and deliveryId. Basic client validation supports the staged flow; it is not address verification or server validation.

Contact validation precedes delivery. Delivery validation precedes quote retrieval and review. A quote contains id, selectionKey, currency, subtotalMinor, shippingMinor, totalMinor, optional discountMinor/taxMinor, and optional expiresAt. The subtotal must match the current supplied lines. The total must equal subtotal minus discount plus shipping plus tax; omitted discount/tax mean zero. Discount cannot exceed the merchandise subtotal. A service with updated item prices must replace the checkout record rather than silently return a different subtotal.

checkoutSelection(checkoutId, value) creates a deterministic address/delivery correlation key. It contains entered destination data. Treat it as private request data, not a URL parameter, public identifier, signature, or authorization proof. A real server must independently verify the cart, address, available delivery, pricing, discounts, taxes, customer access, and payment session. Client totals and correlation keys are not trusted charge instructions.

Quotes with mismatched selection/currency/totals or expired timestamps are rejected. ExpiresAt, when supplied, needs an explicit timezone. Destination/delivery edits invalidate the quote; unchanged contact details do not determine shipping. The summary shows no invented grand total before confirmation. Quote retrieval clears an old quote, so a pending or failed request cannot display stale confirmed totals. Review checks expiry again before handoff and returns to delivery when refresh is required. The UI does not run a live expiry countdown; services must enforce validity at the final handoff.

## Operations and recovery

edit(field, value) updates a known string field and clears that field's error. advance() validates and progresses, requests the quote, or hands the current quote/details to the app. go(contact/delivery) allows backward editing without bypassing validation. Pending work blocks duplicate advance/edit/go operations. Failure retains the draft and provides an announced retry message. Successful handoff disables repeated continuation until editing or replacement.

replace(record, initialValue?) replaces the snapshot, resets the flow, and invalidates stale asynchronous results. cancelPending() invalidates a result locally; it does not cancel a network request or undo external work. Application-owned controllers can outlive a mounted block; the block removes its subscription on unmount. Applications must coordinate cancellation, route changes, session changes, and service idempotency.

The optional continueCheckout callback receives copied checkout ID, value, and quote data. It should open or prepare the application's payment session. Without it, review remains available but the final action is disabled. Resolving the callback means handoff, not payment success. Checkout01 never collects card credentials, authorizes payment, or marks an order paid.

## Core work and preview

Core Stepper now has React parity, a shared bounded progress model, stable keys for repeated labels, and an accessible progress label. It remains a read-only indicator; the controller owns validation and navigation. Core Radio adds native id, required, labelledBy, describedBy, and invalid support in both frameworks, allowing option titles, descriptions, prices, and group errors to be linked correctly.

The preview uses a fictional delivery service and local handoff panel. About this preview can fill fictional details, simulate delivery/handoff failure, or reset the flow. The sample quote adds a supplement for Ireland. Values stay in tab memory. Tests cover minor-unit arithmetic, validation, correlation/expiry, stale/duplicate requests, both framework renders, linked controls, delivery choice, review, and failure recovery. Token checks, typechecks, and production builds complement those checks. Browser optical and native-keyboard review remains pending when no review connection is available.
