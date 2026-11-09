# ProductGallery

Status: **experimental, unreleased development source**. Available in both Vue and React, including the Vue auto-import resolver. This component requires the next core, design, and framework package releases; it is not present in the currently published versions.

ProductGallery is a reusable media control, not a product layout. It composes ProductMedia and Flex, while ProductPage01 remains the registry layout. Images, identity, alt text, and optional selection belong to the application.

## Images and selection

Pass an `images` array of `{ id, src?, alt, thumbnailSrc? }`. IDs must be unique and non-empty. Describe each view with useful alt text. Thumbnails use decorative images inside labelled native buttons, so there is no duplicate image announcement. The selected button exposes `aria-pressed`. Tab, Enter, and Space use native button behavior; this is not a tablist.

By default the component manages selection locally. In Vue, use `v-model` for app-controlled selection. In React, pass `modelValue` and `onModelValueChange`. Controlled selection emits a request and waits for its owner. Reordering preserves selection by image ID. An absent or removed selection displays the first image. Empty galleries and missing or failed sources use ProductMedia's fallback. One-image galleries omit thumbnail controls.

```vue
<ProductGallery :images="images" v-model="selectedImage" label="Linen shirt views" />
```

```tsx
<ProductGallery images={images} modelValue={selectedImage}
  onModelValueChange={setSelectedImage} label="Linen shirt views" />
```

Override `label`, `imageLabel`, and `fallbackText` to localise the component. Image changes also update a screen-reader status with the selected description and position. No autoplay, zoom dialog, or gesture-only interaction is added.

## Tokens

- `--commerce-gallery-thumbnail-size`: thumbnail width, initially derived from spacing.
- `--commerce-gallery-gap`: spacing between the main image and thumbnails.
- Existing image ratio, fit, media radius, border, brand accent, background, and focus tokens control the rest.

Thumbnails wrap on narrow widths. Recipes and presets continue to control appearance. Asset colours belong to the replaceable artwork; interface styling uses design tokens.

## ProductPage01 integration

Pass optional `product.images`. Omitting it preserves `imageSrc`/`imageAlt` behavior. An explicitly empty array shows the missing-media state. Changing product identity resets the gallery. Purchasing snapshots the image list along with the selected product and inventory.

The playground's **In progress** section includes `?preview=product-gallery`; `?preview=product-purchase` also includes multiple views. The sample detail view is a crop of existing local SVG artwork, not a new product photo.

Core selection tests, both framework rendering tests, and Vue client interaction tests cover the behavior. Browser visual, keyboard, and screen-reader review remains pending.
