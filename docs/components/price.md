# Price

Price formats product amounts with `Intl.NumberFormat` in Vue and React. Pass major units: `48.5` means GBP 48.50, not 48.5 pence. Always supply `currency` and `locale`; use the same values on server and client.

```vue
<Price :amount="48" :compare-at="65" currency="GBP" locale="en-GB" />
```

```tsx
<Price amount={48} compareAt={65} currency="GBP" locale="en-GB" />
```

Import from `@paraxe/vue` or `@paraxe/react`. `PriceProps` and the shared `formatPrice` utility are exported by `@paraxe/core`.

| Prop | Type | Default |
| --- | --- | --- |
| amount | number, required | Major currency units |
| currency | string, required | Three-letter currency code |
| locale | string, required | Explicit Intl locale |
| compareAt | number | Omitted |
| size | inline, detail, display | inline; detail and display use shared semantic typography roles |
| currentLabel | string | Current price |
| originalLabel | string | Original price |

A compare-at value above the current amount displays as a struck-through original price. Equal/lower values, or values that round to the same displayed price, are omitted. Zero is valid. Negative/non-finite amounts and compare-at values throw `RangeError`; invalid locale/currency syntax also throws rather than silently changing a price. Currency precision follows Intl (for example, JPY has no fractional digits). Currency conversion, discounts, tax, and money arithmetic belong to the app.

Screen-reader labels distinguish current/original prices without relying on strikethrough announcement. Translate the labels in non-English interfaces. The component adds no live region; announce cart updates at the cart level. Gap and muted text use shared theme/density tokens.
