# ProductCard

ProductCard combines product media, a title link, category, badge, price, availability, and independent actions. Import from `@paraxe/vue` or `@paraxe/react`. The core `ProductCardProps` contract extends [Price](price.md).

```vue
<ProductCard name="Linen shirt" href="/products/shirt" image-src="/shirt.jpg"
  image-alt="Natural linen shirt, front view" :amount="48" :compare-at="65"
  currency="GBP" locale="en-GB" badge="Sale">
  <template #actions><Button @activate="addToCart">Add to cart</Button></template>
</ProductCard>
```

```tsx
<ProductCard name="Linen shirt" href="/products/shirt" imageSrc="/shirt.jpg"
  imageAlt="Natural linen shirt, front view" amount={48} compareAt={65}
  currency="GBP" locale="en-GB" badge="Sale"
  actions={<Button onActivate={addToCart}>Add to cart</Button>} />
```

The app supplies `addToCart` and owns its loading/error feedback. Actions render outside the product link, so buttons and links are never nested by the component. The link always remains available for product details, including when a product is unavailable.

| Prop | Type | Default |
| --- | --- | --- |
| name | string, required | Product title |
| href | string, required | Product details destination |
| imageAlt | string, required | Image description |
| imageSrc | string | Missing image placeholder |
| imageFallbackText | string | Image unavailable |
| category | string | Omitted |
| badge | string | Omitted |
| availability | available, unavailable | available |
| unavailableLabel | string | Unavailable |
| actions | ReactNode (React) / named slot (Vue) | Omitted |

Price props (`amount`, `currency`, `locale`, `compareAt`, `currentLabel`, `originalLabel`) pass through. Translate text labels in non-English interfaces. Availability is descriptive: **the app must disable or remove purchase actions for unavailable products**. ProductCard does not enforce inventory, navigate programmatically, or place orders.

Compose cards directly in `.commerce-grid` or Grid with stretch alignment. Natural text wrapping preserves long titles; actions align at the bottom of cards in each equal-height row. Card padding/radius and default surface treatment use the shared appearance system. Image ratio/radius are independently customizable through commerce tokens. `--product-card-gap`, `--product-card-title-size`, and `--product-card-badge-inset` control the product presentation.

The title renders as `h3`; use it beneath a collection `h2`. Empty states and whole-card skeletons belong to the collection view. Both playgrounds include sale, unavailable, long-name, missing-image, and broken-image samples. Desktop/mobile visual review, keyboard review, and actual image-error recovery checks remain pending before blocks depend on this component.
