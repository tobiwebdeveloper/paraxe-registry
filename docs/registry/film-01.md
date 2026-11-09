# Film01

A film-release layout for independent cinema, documentary projects, and visual storytelling. An offset portrait poster sits beside a large typographic introduction, followed by a practical film-details band, split synopsis, visual contact sheet, compact production credits, and viewing destinations.

Try `?preview=film-01&profile=cinematic&theme=dark` in either playground. It is a development block, not part of immutable registry 0.1.2.

## Recipe and palette

Cinematic suggests Manrope headings, DM Sans body text, small restrained actions, comfortable density, and the Nocturne base with a rose accent. These are optional setup suggestions. Changing only the recipe preserves existing project choices. The block works with other recipes and palettes.

Nocturne is a separate base-color family: `#120e1b` in dark mode and `#fbf9fc` in light mode. The theme generator derives text, borders, surfaces, menus, and feedback from those backgrounds. It does not add a block-local dark skin. Select it in Recipe studio's Base palette field or save `baseColor: "nocturne"` in the preset. It can accompany any recipe.

## Editable content

Both frameworks accept the same `Film01Props`:

- Identity: `studio`, `studioHref`, `eyebrow`, `title`, `tagline`, `year`, `duration`, `language`, `genre`.
- Artwork: optional `posterSrc`, `posterAlt`, `imageCredit`. Without imagery, a duotone concept illustration builds a passage, reflected light, and a solitary figure through perspective. Its ink, light, and tint come from semantic tokens. Supplied posters are shown without decorative overprinting. Titles support newlines.
- Visual notes: `frames`, each with `id`, `label`, `caption`, optional `src`/`alt`, and optional concept-art choice (`passage`, `shore`, or `light`). Three samples form a contact sheet with aligned image heights. Supply real stills or use an empty array to omit it.
- Story: `storyTitle`, `paragraphs`, `quote`, `quoteAttribution`. An empty quote removes it; empty paragraphs show an honest forthcoming state.
- Media: `trailerSrc`, `trailerPoster`, `trailerTracks`, `trailerDescription`. The trailer section and navigation link render only when a source exists. Without one, the primary action leads to the story; no empty player card is shown. Connected media uses shared Video captions and error handling.
- People: `credits`, each with unique `id`, `role`, and `name`.
- Distribution: `viewings`, each with unique `id`, `label`, `detail`, and optional `href`; optional `pressHref` and `notice`.

Empty credit/viewing arrays remove those sections and their navigation links. IDs must start with a letter or digit and contain only letters, digits, underscores, or hyphens. Replace all fictional credits and notices before publication.

## Composition audit

The initial version gave a generic background illustration, unavailable trailer, and supporting headings too much equal space. This was a block-composition problem. The revision separates poster and typography, introduces a visual contact sheet, tightens secondary sections, and omits optional media until it exists. Cinematic uses the shared tighter heading line-height role; Nocturne and other palettes remain unchanged. Artwork is local illustration code, not a new core composite.

Viewing links and press links render only when supplied. No ticketing, streaming entitlement, analytics, content licensing, or video hosting is provided. The app owns those integrations and destination validation.

## Core audit

React Video previously rendered a children-only wrapper while Vue exposed a native player. Development now gives both the shared media contract, captions/subtitle tracks, preload choice, source-change recovery, an optional play overlay, and rejected-play feedback. Video geometry and colors now consume shared tokens. See [Video](../components/video.md).

The hero, story, credits, and viewing rows use Flex composition. Narrow screens stack the story and viewing columns; credits wrap and then become a single column. All interface color, type, space, corners, and controls consume shared roles.

## Validation

Both framework renders are checked for connected anchors, escaped text, explicit sample states, supplied media/tracks, genuine destinations, and empty content. Client tests cover rejected playback, failed-media recovery, pending play, and stale source requests. Token-policy checks, recipe independence/sharing tests, typechecks, and builds cover integration. Browser visual and actual media decoding review remain pending because no browser connection is available.
