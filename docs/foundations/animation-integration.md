# SVG and animation integration plan

Keep assets replaceable and animation optional. Static SVGs can already be supplied through Image, ProductMedia, logo props, or registry media slots. SVG source and Lottie animation data are distinct assets: Lottie-web loads animation data and can render through SVG, canvas, or HTML; it is not a player for an arbitrary standalone SVG image. See the [official Lottie-web options](https://github.com/airbnb/lottie-web/wiki/loadAnimation-options).

## Layer boundary

1. **Core contract:** propose a renderer-neutral Animation contract for source/data, poster, accessible label/decorative mode, play/pause, loop, speed, readiness/error callbacks, and reduced-motion behavior. Keep timing/loop state explicit. Do not place animation JSON or player dependencies in structural tokens.
2. **Optional adapters:** add Vue/React adapters behind optional package entry points or a separate animation package, with a Lottie adapter first. Select/pin a runtime only when implementing that adapter; no player is installed by this plan. Static component consumers should not download a player.
3. **Registry composition:** a hero owns placement and content. Its media slot can accept an animation component; the player must not own hero headings, CTAs, or page layout. Blocks declare animation/assets as dependencies only when they actually use them.

## Runtime requirements

- Render a stable-size poster/fallback on the server; load the player on the client only when needed.
- Prefer a static poster when reduced motion is requested, with an explicit user play option where appropriate. Do not treat an OS preference as permission to remove essential content or interaction. W3C documents [prefers-reduced-motion as a technique for preventing interaction motion](https://www.w3.org/WAI/WCAG22/Techniques/css/C39).
- Support pause/stop for looping decorative content; avoid making essential meaning depend on animation.
- Pause when offscreen/backgrounded, clean up listeners/player instances on unmount, and handle source changes without leaving old renderers behind. Lottie-web provides lifecycle controls including destroy; see the [official README](https://github.com/airbnb/lottie-web/blob/master/README.md).
- Keep decorative animations out of the accessibility tree. Informative animations need a text equivalent or stable label; avoid announcing every frame.
- Handle failed loads through the same poster/fallback geometry. Expose failure to the app without breaking the containing block.
- Keep renderer choice and asset paths explicit. Do not promise automatic recoloring of arbitrary JSON/SVG data; use designed theme variants or supported adapter mappings.

## Implementation order and release gate

First agree the contract and test a small local animation fixture. Then implement both adapters, reduced-motion/poster behavior, controlled playback, lifecycle cleanup, and SSR tests. Finally add one opt-in hero example and review keyboard behavior, CPU/bundle impact, narrow-screen sizing, color contrast, and pause controls in a browser. Keep a static equivalent available.

Hero01 is ready for replaceable media today. A Lottie runtime, importer, animation editor, or conversion pipeline is not implemented yet.
