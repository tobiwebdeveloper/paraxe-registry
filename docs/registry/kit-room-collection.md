# Kit room collection: reference detail map

Reference supplied in chat: a monochrome collection at approximately 1307 × 959px, showing a left filter rail and three product columns. The measurements below are estimates from that image, not sampled design-file values. The implementation lives at `registry/blocks/kit-room-collection/`, registered as `kit-room-collection`; both playgrounds import those exact sources.

## Every visible part

| Reference detail | Paraxe building block | Registry recipe/behavior |
| --- | --- | --- |
| Off-white/white canvas, almost-black ink, quiet grey separators | Design theme tokens | Inherit accent/foreground/surface tokens and light/dark mode. Choose monochrome in the preset to match the reference. |
| Roughly 40px outer horizontal inset | Block root | Spacing-token padding, reduced at tablet/mobile. |
| Tiny uppercase “THE KIT ROOM” eyebrow | Text | 10px equivalent, semibold, tracking 0.1em; grouped with the title using column Flex. |
| “Find your next essential.” headline | Heading h2 | Approximately 36px at desktop, tight tracking/line height; fluid down to 28px. Separate muted full stop. |
| Right-aligned supporting sentence on the headline baseline | Text + row Flex | `justify="between"`, `align="end"`, wrapping on narrow screens. |
| Four category tabs | Tabs + Tab | All products, Training wear, Outerwear, Accessories; explicit underline variant and keyboard navigation. |
| Small square count next to All products | Badge inside Tab | Count comes from the eight-product fixture; small neutral fill, no pill radius. |
| Thin continuous rule below tabs, active dark underline | Tabs design CSS | Block-scoped tab gaps/padding; active state uses monochrome brand ink. |
| Filter rail around 190px wide, about 36px from results | Flex | A fixed-basis aside beside a fluid, `min-width: 0` results area. |
| “Filters” at left and small underlined “Reset all” at right | Heading + Button text + Flex | Reset clears tab, facets, size, price, stock, search, and sort. It is a real button, not an anchor. |
| Section separators | Border token in recipe | Category, Size, Price range, Availability each have an upper hairline and token padding. |
| Category checkbox rows with counts at the far right | Checkbox + inline span Flex | Fixture counts are 5 training, 2 outerwear, 1 accessory; multiple categories combine as OR. |
| Small empty square checkbox geometry | Checkbox | Block recipe reduces the square to the visual reference; focus remains the shared control focus treatment. |
| Six size tiles wrapping onto a second line | ChoiceGroup + Choice + Flex | XS, S, M, L, XL, One size; `multiple`, auto width, small size. No separate picker composite. |
| Upper-bound price labels (£0 / £100) | Text + Flex | Maximum updates with the slider; currency is GBP for this fixture. |
| Dark filled range track and round thumb | Slider | Range 0–100. React receives the missing Slider counterpart; labels remain programmatically available. |
| “In stock only” row | Checkbox | Excludes the two unavailable fixtures when selected. |
| Quiet promotional card with diagonal arrow | Flex + Heading + Text | Recipe owns the neutral fill and wording; arrow is decorative text, not a fake action. |
| Small result count at the top-left of results | Text | “8 essentials / 8 products” initially; polite live region updates only the result count. |
| Small “Sort by” label and borderless native selector | Select + labelled Flex | Featured, price ascending/descending, and name; native label association. |
| Full-width thin-bordered search row | Input + Flex + Text | Search glyph at left; real hidden label, flexible input, small “FIND YOUR KIT” suffix at right. |
| Three equal product image columns with narrow horizontal gutters | Grid | Three/two/one columns at desktop/tablet/narrow mobile, not a row of manually positioned cards. |
| Tall, square-cornered neutral product image area | ProductMedia | Ratio 1 / 1.12; local SVG product illustrations; image and placeholder geometry match. |
| Black/yellow garments, grey hoodie, black kit bag | Registry-owned assets | Eight standalone SVG fixtures. These are editable sample artwork, not catalog photos or library assets. |
| Tiny “CONCEPT” label at the image top-left | Badge | Absolutely positioned within the image wrapper with 12px token inset. |
| White circular diagonal arrow at the bottom-right | Decorative link affordance | Part of the product link, not a nested button or second interactive action. |
| Tiny muted category below each image | Text | Natural wrapping with small token spacing above the title row. |
| Product name and right-aligned price on one baseline | Heading h3 + Price + Flex | Title can wrap; price is kept together. Explicit `en-GB`/`GBP` formatting. |
| Availability/size count under each product | Text + Flex | Five sizes or One size where applicable; unavailable fixtures say so explicitly. |
| Tiny outlined color dot at the lower-right | Swatch | Standalone reusable atom with optional accessible label; not a product-block-specific control. |
| Next row remains aligned and continues below viewport | Grid | Natural card heights, no masonry positioning or forced clipping. |

## Interaction and responsive rules

Search, tab, category, size, maximum price, and availability filters intersect. Multiple categories/sizes use OR within their own facet. Counts beside categories describe the whole fixture (the reference's 5/2/1), not a dynamically shrinking facet count. Sorting operates on a copy and never changes catalog order. Empty results offer a text-button reset.

Product selection opens a small inline preview and emits `product-select` (Vue) / calls `onProductSelect` (React). Consumers can replace that with navigation. Fixtures do not place orders or claim real inventory. The block owns this application behavior; Price, Swatch, or Choice must not acquire catalog logic.

At 64rem, the product grid becomes two columns and the rail narrows. At 48rem, filters collapse behind a labelled button placed before the rail in reading order; `aria-expanded`/`aria-controls` expose the state. At 26rem, products use one column. Search suffix text hides on mobile; tab labels scroll horizontally. Tabs and their shared results panel have IDs/ARIA associations, generated per block instance.

## Preview and customization

Run the Vue or React playground and open `?preview=kit-room` for the isolated light-mode collection. The existing Vue Commerce page also previews it with the rest of the component lab. Change the preview's theme state to inspect dark mode. The block inherits the design stylesheet/preset/theme setup; no duplicate global reset is shipped in its registry files.

Edit shared fixture/data logic in `shared/collection.ts`, block styling in `shared/collection.css`, and the framework entry to change composition. Customize the filter width, layout/grid gap, image surface/ratio, text, and source data at block level. Use public component tokens for individual control shape/spacing. Copy assets to their manifest `public/` targets when consuming the registry bundle.

Source checks cover filtering, sorting, asset paths, registry containment, component rendering, and framework builds. Desktop/mobile screenshots, native keyboard/form behavior, color contrast, and touch-target review remain pending. The visually small reference controls/text are not a blanket accessibility approval; adjust typography and target sizes for the product's requirements.


The measurements above describe the reference, not values pinned into the block. Its current CSS consumes core semantic typography, media radius, form option spacing, and commerce layout roles. Use the editorial recipe and compact density for that treatment; changing a preset must still change the block. See [recipe architecture](../foundations/recipes.md).

## Collection filtering development

The collection now exposes removable active filters for category tabs, category facets, sizes, price, availability, and search. Removing one constraint preserves the others and the current sort order. Whitespace-only search and sorting alone do not count as filters. Active filter labels wrap and inherit core Button tokens.

On small screens the existing disclosure includes the active count and a ?Show results? action. Closing that way focuses the results panel; Escape returns to the filter trigger. Removing a filter focuses the next remaining filter button, or search when none remain. The decorative sidebar note is omitted on small screens so the controls remain the priority.

The desktop composition and Flex-based responsive structure remain intact. No new drawer or composite is needed. Find the development preview under **In progress ? Collection filters** or open `?preview=kit-room` in either playground. Published registry 0.1.2 bundles remain unchanged.

Automated coverage includes isolated filter removal, sort preservation, empty-result recovery, both frameworks' rendered controls, and Vue client interactions. Browser layout and keyboard review remains pending.

Apps can now pass `productHref(product)` for normal product-route anchors. This bypasses the local preview panel and preserves native link behavior. The [connected shop](shop-journey.md) demonstrates the integration.
