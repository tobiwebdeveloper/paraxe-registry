# ProductMedia

ProductMedia reserves a product image ratio and displays a stable placeholder when an image is missing, pending, or fails to load. Import it from `@paraxe/vue` or `@paraxe/react`.

```vue
<ProductMedia src="/shirt.jpg" alt="Natural linen shirt, front view" />
```

```tsx
<ProductMedia src="/shirt.jpg" alt="Natural linen shirt, front view" />
```

| Prop | Type | Default |
| --- | --- | --- |
| src | string | Missing image placeholder |
| alt | string, required | Use a meaningful description, or empty for a decorative image |
| pending | boolean | false |
| fallbackText | string | Image unavailable |

Images load lazily and decode asynchronously. A failed source falls back to text; changing the source permits another load. Pending media sets `aria-busy` and uses a labelled placeholder without requesting the image. Translate `fallbackText` as needed. The pending flag is controlled by the app; this component does not fetch product data or retry a failed URL automatically.

Override `--commerce-image-ratio`, `--commerce-image-fit`, and `--commerce-image-radius` on a wrapper. The same geometry is reserved for normal and placeholder states. Default photography is square-cornered independently of card radius.

Image-error recovery still needs browser interaction coverage; server rendering checks cover the missing and pending states.

Development addition: `as="span"` renders phrasing content for labelled thumbnail buttons. The default remains `div`. This option is staged for the next package release.
