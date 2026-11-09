# The Paraxe block-and-recipe formula

The owner endorsed the recent Educational, Swiss/Article01, and Brutalist/Event01 direction on 9 November 2026. The particular quality to preserve is the relationship between typography, buttons, spacing, and the purpose of the page.

## Start with a product job

Choose what someone is trying to make: an event, publication, learning experience, service studio, shop, or member workspace. Identify the page's audience, main decision, and useful next action before choosing visual effects.

A numbered block earns its place through a distinct composition. Event01 has a poster, practical details, programme, lineup, and registration boundary. Article01 has a masthead, editorial header, reading measure, contents rail, and source/author notes. Pricing01 and the kit collection each solve another clear layout job. A connected journey is an example; it does not count as a new block.

## Develop the layout and flavour together

Work out the silhouette: major type, column proportions, aligned edges, section rhythm, and the balance between quiet areas and concentrated detail. Give the main action a clear position. Define desktop and narrow-screen arrangements together. Prefer Flex where it suits the composition.

Choose an existing recipe when it fits. Add a recipe when a different reusable typographic/control treatment is justified. Educational makes guidance approachable; Swiss gives information hierarchy and precision; Brutalist gives Event01 expressive type and tactile controls. The same block should remain usable under other recipes.

A recipe is not a palette lock. Colour, font family, radius, density, card surface, and variants remain independently editable. Suggested profiles are opt-in starting points; explicit user choices win.

## Preserve the typography/control relationship

The owner particularly values the typography and buttons in Educational, Swiss, and Brutalist. Treat their balance as part of product quality rather than incidental decoration.

Use expressive display type to establish the main idea, readable body type to carry the explanation, and smaller, more compact button labels to make actions feel deliberate. Weight, line height, letter spacing, padding, minimum height, border, and depth all contribute. A different font's x-height changes the visual result even at the same numeric size.

These are source-token baselines, not browser measurements. Assuming a 16px root and comfortable density:

| Treatment | Display/hero range | Medium button label | Label weight | Button minimum height | Decoration |
| --- | --- | --- | --- | --- | --- |
| Educational | 48-72px, inherited responsive role | 14px | 600 | 44px | 4px token-derived lower edge |
| Swiss | 48-88px responsive role | 12px | 600 | 44px | Quiet, precise rule treatment |
| Brutalist | 52-120px responsive role | 14px | 700 | 44px | Strong borders and 4px offset shadow |

The minimum-height/label-size ratios are about 3.14 for Educational/Brutalist and 3.67 for Swiss at that baseline. These are useful observations, not fixed targets. Padding, wrapping, root size, selected density, and font metrics can change the rendered height. Shadows add perceived mass without increasing the layout box.

For new flavours, tune the relationship across display, section headings, body, and controls. Avoid sizing all text up together or making buttons visually compete with the title. Keep the established recipes intact unless there is evidence of a defect. Judge wrapped labels and long headings as well as short specimen text.

## Audit and improve the core

Check semantics, behavior, attribute forwarding, styling roles, and Vue/React parity before writing local exceptions. Reuse atoms and focused controls. Put reusable improvements into core: Progress naming/bounds, Image loading/failure states, media ratio tokens, and form accessibility are examples. Avoid new composites that only rename one composition.

Blocks consume tokens and may expose local composition aliases. They do not overwrite foundation palettes, fonts, radius, or density. Brand marks, imagery, copy, dates, prices, and destinations must be replaceable.

## Make the layout useful

Handle empty, unavailable, long-content, pending, failure, and recovery states that matter for the job. Use real anchors where possible. Enable submission, registration, authentication, or purchase only through a real supplied integration. Keep persistence, authorization, pricing, payments, content access, and transport owned by the application.

Build both frameworks, register source files and assets, document the job and API, and expose the block and its intended recipe in the playground/gallery. Label examples, components, recipes, and blocks accurately.

## Verify honestly

An optional missing integration should not become a dominant empty card. Film01's first version failed this test: the artwork was generic, supporting sections had similar visual weight, and the unavailable trailer weakened the page. The revision gives the poster and title a clear relationship, uses a visual contact sheet, and renders the trailer only when supplied. A fallback is a recovery state, not a substitute for the block's main composition.

Check token consumption, preset sharing, independent axes, semantic structure, and meaningful behavior. Typecheck and build both frameworks. Review desktop/mobile, light/dark, contrasting palettes, long text, native focus, and actual font loading in a browser when available. Compilation and arithmetic do not prove optical balance; record visual-review limits explicitly.

Current limitation: connected browser review has been unavailable. User feedback on the recent layouts is positive, while automated verification and browser-review status remain separate records.

## Brief for the next addition

The owner endorsed the revised Film01 and clarified the principle: a style has a particular character they can feel even when it is hard to name. Treat that character as a relationship between layout, artwork, type, controls, and pacing. Do not apply the same composition and illustration to every new recipe. Hospitality, for example, benefits from an inviting landscape, tactile details, readable room comparisons, and clear planning controls; it should earn a different silhouette from a film poster or event programme.

Record: product job; distinctive layout; intended recipe; typography/control proportions; core gaps; editable data and integration boundary; narrow-screen structure; important states; validation and release status.

The owner has asked to continue this pattern. Keep new blocks distinct, flavours purposeful, and preset flexibility intact. Significant changes to the agreed product direction should be discussed; routine implementation within it can proceed.

## Font feedback: family versus weight

The owner clarified that lighter Fraunces works for Studio; bold Fraunces does not. Keep that font family and correct weight consumption before substituting another font. Heading roles must actually reach the rendered classes. Studio uses regular (400) headings, while existing profiles retain their previous weights. This feedback concerns the optical weight of the display text, not a request to change button or body proportions.

## Cinematic and Nocturne

Film01 gives the formula a culture/film context: one dominant title frame, quieter practical details, narrative reading space, a real trailer integration, and clear production/distribution sections. Cinematic suggests Manrope at regular weight with a responsive 56-144px hero range and 12px medium button labels. Comfortable medium controls retain the shared 44px minimum; their baseline height/label ratio is about 3.67. These are source-token observations, not browser measurements.

Nocturne is a separate base palette, not part of the recipe CSS. Its dark plum and warm light counterpart feed the existing color derivation engine. Recipe-only changes preserve the base and every other explicit project choice.

## Organic and hospitality

Stay01 combines a broad landscape, an italic display phrase, a compact planning form, measured room comparisons, and quieter house details. Organic suggests regular Lora headings and Work Sans body text, with 12px uppercase medium button labels against a 44px comfortable minimum control height. The hero role spans 48-96px. These source-token proportions preserve an inviting reading pace without enlarging every control. Palette, type family, radius, density, and surfaces remain editable. The original photograph is replaceable content; it does not freeze the interface palette.
