# Studio01

A standalone service-studio website in Vue and React, pairing a type-led introduction with selected work, capability disclosures, and a project-enquiry form. It extends Paraxe into professional services and independent creative practices.

## Composition and proportions

The hero gives the display typography room, then places the supporting statement beside one clear enquiry action. Selected studies use equal-width Flex columns and replaceable imagery or typographic artwork. A split approach section uses the shared Accordion for service details. The final section places a project brief beside a clear invitation.

The Studio recipe is a quieter alternative to Swiss and Brutalist. Its optional profile suggests Fraunces headings, DM Sans body text, stone neutrals, a teal accent, larger corners, spacious density, and flat card surfaces. The recipe itself does not impose any of those axes.

Its source-level baseline uses a responsive 48-96px hero range and a 14px medium-weight button label at a 16px root. The suggested spacious profile supplies a 52px medium-control minimum height. These are design inputs, not browser measurements or a universal ratio. See the [block-and-recipe formula](../block-and-recipe-formula.md).

## Editable content

Replace the studio name, location, hero copy, availability text, selected projects, services, enquiry copy, labels, privacy destination, and notice. Concept studies are explicitly labelled as samples; no client credentials or testimonials are invented.

Projects have unique IDs, titles, category/year, description, replaceable typographic mark, optional image/alt text, and optional case-study destination. An image uses the shared media-video ratio token. A project becomes a link only when a real destination is supplied. Services have IDs, titles, descriptions, and deliverables. Empty projects/services have explicit states.

All interface colours, type, spacing, radius, surfaces, and focus consume tokens. `--studio01-column-gap` and `--studio01-section-gap` expose composition rhythm. On narrow screens the introduction, projects, approach, enquiry columns, and paired fields stack.

## Enquiry boundary

Supply `submitBrief(brief)` to enable submission. The callback receives a fresh trimmed snapshot of `{name,email,serviceId,message}`. The selected service must exist in the current service list. Native required/email semantics complement shared validation; server-side validation remains application-owned.

The callback may return a promise. Controls lock while pending and duplicate submissions are prevented. Rejection preserves the draft and shows a generic error; success clears the fields. No enquiry is sent without a supplied handler. Empty services disable new enquiries. The block owns no email service, CRM, persistence, analytics, or contact list. Labels and result messages are replaceable. A privacy link appears only if supplied.

## Core improvements

Select now exposes required, described-by, and invalid attributes in both frameworks. FormField exposes `id-description` and `id-error` helper targets and an alert role for errors; its consumers explicitly connect those targets through `describedBy`. React Text forwards native/ARIA attributes so helpers can carry stable IDs. These changes are reusable and staged for the next core/framework/design release.

## Preview and validation

Open `?preview=studio-01` in either playground, or `?preview=studio-01&profile=studio` for the optional Studio profile. Both appear under In progress in the registry gallery.

Checks cover source identities, validation and snapshotting, real project destinations, empty content, native form semantics/helper targets, duplicate prevention, rejected-draft preservation, and successful reset. Both frameworks are typechecked and built. Recipe checks preserve independent axes and sharing. Browser visual, actual-font, keyboard, and responsive review remains pending. The source is not part of immutable registry 0.1.2 bundles.

### Heading-weight correction

Fraunces remains the suggested display font. Core Heading classes now consume per-size weight roles; Studio maps those roles to its regular weight (400). This corrects headings that previously bypassed the lighter recipe and rendered bold. Other recipes retain their previous Heading weights. Body text and button proportions are unchanged.
