# Invoice01

A client-facing invoice document with issuer/client identities, date band, native line-item table, exact totals, payment ledger and separate amount-due summary. Suggested recipe **Swiss**, with all preset axes independent. This is a billing document layout, distinct from the operational order list.

**Development after registry 0.3.0.** [Vue](https://tobiwebdeveloper.github.io/paraxe-registry/preview/vue/?preview=invoice-01&profile=swiss&theme=light) / [React](https://tobiwebdeveloper.github.io/paraxe-registry/preview/react/?preview=invoice-01&profile=swiss&theme=light). The preview uses fictional data and never requests or processes payment. It can show part-paid, paid, overdue and void examples and generate the displayed CSV breakdown.

## Supply the invoice

Copy renderer, shared/invoice.ts and shared/invoice.css together. React accepts invoice={record}; Vue accepts :invoice="record". Replace issuer/client names, address lines, copy, dates, reference, line items, payment records and instructions. No brand/logo is fixed to a reference shop.

All monetary inputs are nonnegative safe integers in **minor units**. Each line has unique ID, title, optional description, positive integer quantity and unitMinor. Supply taxMinor and discountMinor explicitly; no tax rates or jurisdiction rules are inferred. Payments have unique ID, label, calendar date and amountMinor. The view computes subtotal, total, paid and outstanding with safe-integer checks. Currency precision comes from Intl for the supplied currency/locale; display conversion is separate from charge creation.

Dates are actual YYYY-MM-DD values, formatted in UTC; due cannot precede issue. state is open/overdue/void. Overdue is app-supplied, not inferred from the visitor's clock. Fully settled open invoices display Paid. Voids have no payment due; this layout rejects voided paid invoices and overpayments because refund/credit handling requires a different authoritative model. This is not accounting, tax or invoicing compliance software.

paymentHref is optional and must be a relative or HTTPS destination. The Pay invoice anchor appears only when an actionable balance exists. Your app owns authentication, authoritative balances, payment links, authorization, payment processing and reconciliation. Omit a destination to hide the action. The block never invents a payment confirmation.

## Breakdown and layout

Download breakdown generates a real UTF-8 CSV data resource from the displayed record. The file declares currency and minor-unit amount columns, escapes CSV quotes and prefixes obvious formula-like string cells. It is a breakdown, not a generated legal invoice PDF. No print/PDF backend is implied.

The layout is one framed billing document: an identity masthead, invoice/reference header and real CSV action, a full-width amount-due band with aligned totals and dates, then a broad deliverables table beside a quieter billing/history rail. The note and totals form a closing settlement row. These are Flex regions; dates/addresses wrap. A real table retains row/column headings and can scroll horizontally on small screens. Summary prices consume core Price with an Amount due label and room for larger recipes. The sheet consumes card background/radius/shadow roles. A token-derived brand band provides emphasis; billing details and the connected payment timeline share a supporting surface. The narrow table region is labelled and keyboard-scrollable. --invoice01-gap and --invoice01-sheet-padding are local composition hooks. Paid/void states remove payment actions and do not conceal the supplied record.

Tests cover exact totals, currency precision, safe arithmetic, invalid configuration/destinations, paid/void states, actual CSV data and both framework renderers. Browser visual review remains pending when unavailable.

Development Price also accepts amountMinor and compareAtMinor instead of major-unit amount/compareAt. Supply exactly one unit mode. Nonnegative safe integers format through BigInt parts, preserving cents even at the safe-integer boundary and respecting currency-specific precision. Invoice01 uses this mode for its amount-due display; published packages still have the earlier major-unit-only API.
