# Orders01

An order-management workspace with a searchable order book, fulfilment tabs, global sorting, pagination, CSV export, and an in-flow detail panel. The detail includes product lines, app-supplied totals, payment status, customer/delivery information, and timestamped activity. Swiss is its suggested recipe; existing palettes, fonts, density, radius, and surfaces remain configurable.

Try `?preview=orders-01&profile=swiss&theme=light` in either playground. Included in registry **0.3.0**, with core **1.6.0**, design **1.10.0**, Vue **1.5.0** or React **0.4.0**, and CLI **0.5.0**. Its shared component improvements ship in these packages. Older immutable registry 0.2.0 does not include this layout.

## Use and data ownership

Import the named Orders01 React entry or the default Vue entry. Optional props are orders, currency (GBP), locale (en-GB), title, pageSize (6), loading, error, and retry. Omitting orders uses illustrative sample data; pass an empty array for a real empty collection. One currency applies to the supplied order book. The page size can be changed by the app and is bounded to 1–50. Currency/locale formatting and UTC timestamps are explicit, so server/client rendering agrees.

An OrderRecord has a unique id, display number, createdAt, fulfilment status, payment status, customer, lines, totals, delivery, and events. Amounts are major currency units. The app supplies line amounts and subtotal/shipping/tax/discount/total; the block does not calculate charges, refunds, tax, or fulfilment changes. Totals are displayed as supplied rather than implying a client-calculated financial ledger. Customer and address records must be authorized before delivery to the browser.

Tracking codes remain text unless a real HTTPS trackingHref is supplied. Customer email opens a normal mailto link. Sample images are copied with the block and can be replaced per line; Image provides missing/error fallback. No carrier, payment, or customer-message API is called by the block.

The optional order-select event (Vue) / onOrderSelect callback (React) reports an order when its number is activated. Do not mutate its record; replace the orders prop when app data changes. The optional retry callback is the only reason a retry button is shown. The parent owns refreshing data and the loading/error state.

## Interaction and layout

Search covers order number, customer name/email, and product name. Fulfilment filters and global sorts apply to the full supplied collection before pagination. Counts describe the supplied collection, not an unseen server dataset. This is client-side paging; implement server query/paging deliberately for a large order service.

Changing filters, pages, or records clamps the page and reconciles detail selection to a visible row. The detail can be closed without leaving the order book. Order numbers are real keyboard-operable buttons with linked expanded states. Opening details moves focus to its labelled section; closing restores the opener when it still exists. On smaller screens the detail follows the list in normal flow, with a focus/scroll transition. It does not pretend to be a modal drawer.

Export results downloads the current filtered/sorted collection, including all matching pages. It does not export hidden unmatched orders. CSV fields are quoted/escaped and potential spreadsheet formulas are neutralized. A download happens only after the user activates Export results. Apply your own export permissions and privacy policy before rendering sensitive data.

Loading hides stale order/detail content; errors hide customer details and offer retry only when wired. Empty collections and zero filtered results have distinct messages; Clear filters restores the supplied collection. About this preview lets reviewers exercise loading/error/empty states against explicit sample data.

## Core work

Pagination now shares a bounded paginationState helper across Vue and React. React consumes the same variant defaults, shape, and navigation label as Vue; shared CSS implements outline, filled, minimal, and round treatments. Invalid numeric inputs and huge page windows are bounded rather than creating unbounded DOM or loops. No new visual recipe was added.

Tests cover full-data sorting before paging, search/status matching, selection reconciliation, prop replacement, data validation, CSV safety, both framework renders, linked controls and focus, discount formatting, loading/error/empty states, and pagination parity. Browser visual review remains pending when no connected browser is available.
