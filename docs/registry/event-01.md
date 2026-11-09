# Event01

A standalone event page in Vue and React: poster-led header, arrival details, day-by-day programme, speaker lineup, and a registration panel. It is a new layout, not a wrapper connecting existing pages.

## Layout and core audit

A compact event masthead leads into an accent-filled typographic poster. A separate introduction/date/location band gives the practical details room. The programme uses a time rail and session descriptions beneath day tabs; speaker links target the actual lineup. The registration area splits an invitation and inclusions from pricing and action.

Flex owns the composition. Speakers retain consistent column widths when the last row is incomplete. Monogram artwork and optional portraits share `--media-aspect-portrait`; core media classes now use their existing ratio tokens instead of literal values. Tabs, Image, Price, Badge, Button, Heading, and Text already provide the required core controls.

On smaller screens, practical details wrap, session times move above the description, speaker columns reduce, and registration stacks. Typography, radius, density, surfaces, borders, accent, foreground, and focus follow tokens.

## Editable event data

Props replace the name, edition, title, intro, date mark, date/time label, location, timezone label, days, speakers, registration, and notice. Dates and timezone labels are supplied explicitly by the application. The sample is fictional and does not read the current clock or advertise a real event.

Each day has a unique anchor-safe ID, labels, and sessions. Sessions have local IDs, ISO date-time strings, displayed times, format, description, location, and speaker IDs. Speaker references must resolve to the supplied lineup. Selection follows day identity across reordering; removed days fall back to the first day. Empty programmes, empty days, and empty lineups have explicit states.

Speakers accept name, role, topic, optional portrait, and optional profile destination. Without a portrait the block uses typographic monograms rather than fake photos. Changing the portrait ratio token also changes monogram geometry.

## Registration boundary

`registration=null` omits the registration section and its navigation link. Otherwise pass heading, description, inclusions, optional major-unit price/currency/locale, price note, action labels, note, and optional real `href`. Zero-priced registrations work. Missing destinations show an unavailable button. Only a supplied destination enables registration navigation.

No payment, booking, seat availability, account access, or ticket email is supplied by this block. The application owns those integrations and authoritative pricing. No outbound network request occurs just by rendering it.

## Recipes and previews

Open `?preview=event-01` in either playground. `?preview=event-01&profile=brutalist` demonstrates the optional Brutalist profile. Recipe studio can change the treatment and every independent axis; the event does not impose yellow, square corners, or a particular font.

Local `--event01-rule` and `--event01-section-gap` aliases expose the composition's rule weight and section rhythm. All new source is staged for the next coordinated release, not included in immutable registry 0.1.2 bundles.

## Validation

Checks cover data identities, speaker references, day switching/reordering/removal, labelled tab panels, native anchor destinations, supplied registration links, empty states, and escaped custom text. Typechecks, production builds, and token guards cover both frameworks. Browser visual, keyboard, mobile, and screen-reader review remains pending.
