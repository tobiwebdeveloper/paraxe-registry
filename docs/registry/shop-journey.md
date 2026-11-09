# Connected shop demo

This is a playground composition of existing blocks, not another registry block. It demonstrates collection ? product ? bag in Vue and React using a single app-owned cart. Find **Connected shop** under In progress, or open `?preview=shop-journey`.

## Try the journey

1. Filter or search the collection and open a product.
2. Choose a size and quantity, then add it to the bag.
3. Use Cart in the navbar to change quantities or remove items.
4. Open a product from the bag or return to the collection. The cart and collection filters remain in memory.
5. Use browser Back/Forward between views, or Reset demo to clear the bag.

Hash routes keep the demonstration independent of a router library and static-host rewrite rules. Unknown or malformed product links recover to the collection. Navigation moves focus to the active view's heading. The collection remains mounted while hidden to preserve local filter/sort state.

## Integration boundaries

CollectionBlock accepts optional `productHref(product)`. With it, product anchors retain native browser navigation, including modified clicks; the local preview panel is bypassed. Without it, existing inline preview behavior stays available.

ProductPage01 receives product data and the add callback. Cart01 receives lines, totals, quantity/removal callbacks, and real product links. Navbar01 receives destinations and the shared count. No block owns the application's cart or routing.

The shared playground adapter derives sample product details and prices from the existing catalogue. Each available sample variant starts with eight units; existing bag quantities reduce the amount available to add. Unavailable fixture products cannot be added. Requests are checked against current local inventory, and line totals use catalogue prices rather than submitted product prices. These checks demonstrate state consistency, not transaction security.

No data persists across reloads. No backend, payment, order, tax, shipping calculation, or authentication is supplied. A production app must use authoritative server-side pricing and inventory. Existing gallery media and brand assets remain replaceable, and all UI styling follows presets and tokens.

## Source and validation

The shared adapter lives in `playgrounds/shared/shop-demo.ts`; each framework has its own `ShopJourney` wrapper. This is development source for the next coordinated release. Published registry 0.1.2 installation bundles remain unchanged.

Automated checks cover cross-product quantities, stock restoration, unavailable items, fixture pricing, route recovery, and app-owned product links. Framework typechecks and production builds cover the composition. Actual browser navigation, focus, desktop/mobile layout, and screen-reader review remain pending.
