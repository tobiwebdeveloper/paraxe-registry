# Article01

A standalone long-form publication block for essays, studio journals, research notes, or company editorial. It adds a new layout to the registry in Vue and React; it is not a composition-demo wrapper.

## Layout and core audit

A masthead and oversized title establish the publication. The standfirst and author/date details form a second horizontal band. The cover can be a replaceable image or a token-driven typographic graphic. A numbered contents rail sits beside a readable text column, with section headings, paragraphs, lists, pull quotes, source notes, and an author footer. A three-column related-reading area closes the page.

On smaller screens the contents becomes a wrapping navigation group, byline stacks below the standfirst, decorative cover numbering is omitted, and related reading stacks. The composition uses Flex. Heading, Text, Badge and Image supply the existing core behavior; a prose or article composite was not needed.

Core Image gained pending, missing-source, failure, and source-change recovery states for this work. Its placeholder uses shared media/surface/type tokens and alt-derived accessible naming. Decorative media remains hidden from assistive technology. Existing eager loading is preserved by default; `loading="lazy"` is available for lower-page imagery. The article requests eager loading for its cover.

## Replaceable content

Pass publication, issue, category, title, standfirst, publication date/time label, reading time, optional author, cover or graphic, sections, sources, related reading, optional journal destination, and notice. Dates and reading estimates are app-supplied.

Sections use unique anchor-safe `id` values, a title, plain-text paragraphs, and optional list or quote. Sources and related stories have unique IDs, titles, detail text, and optional real destinations. Text is escaped by the frameworks; arbitrary HTML is not accepted. This is not a rich-text editor or Markdown renderer.

The default is an original sample essay and theme-driven cover graphic. Pass `cover={src,alt,caption?,credit?}` to replace the graphic with media; missing or broken media receives the core fallback. Pass `graphic=null` to omit the default graphic. `author=null` hides author details. Empty sections receive an explicit placeholder; empty source/related arrays omit those sections. A related story becomes a link only when the application supplies a destination.

Native contents links target actual section IDs, scoped per instance. There is no scroll listener, fake reading-progress percentage, clipboard integration, or required client router.

## Styling

Palette, typography, spacing, radius, surfaces, and focus consume tokens. Local `--article01-reading-width`, `--article01-toc-width`, and `--article01-reading-gap` expose reading composition. The text measure starts from `--content-width-narrow`; the article never fixes the font or forces a white background.

Open `?preview=article-01` in either playground. Use `?preview=article-01&profile=swiss` for Swiss's optional suggested profile. Other recipes remain available in Recipe studio. This source and the Image update are staged for the next coordinated release, not included in registry 0.1.2.

## Verification limits

Checks cover anchor identity, scoped repeated instances, escaped custom text, optional/empty sections, replaceable covers, and core Image pending/failure/recovery behavior. Framework builds, typechecks, and registry token checks cover the registered implementation. Browser visual, keyboard, and desktop/mobile review remains pending because no browser connection is available.
