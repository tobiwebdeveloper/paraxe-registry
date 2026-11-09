# Stay01

Stay01 is a hospitality layout: an editorial introduction, landscape, date-and-guest planner, room comparison with concept plans, and a quieter band of house details. The purpose is to help someone choose the kind of stay they want, rather than imitate a generic app dashboard.

Preview `?preview=stay-01&profile=organic&theme=light` in Vue or React. The block remains a development addition awaiting coordinated release.

## Composition and recipe

Organic uses a distinct field-note treatment: medium-weight Lora headings, small uppercase mono labels, ink-filled primary buttons, and outlined secondary actions. Studio keeps its regular Fraunces headings and quieter 14px mixed-case controls. Organic maps button color roles locally on each component; the global palette and all other preset axes stay editable. The sample profile suggests Stone, Amber, comfortable density, larger corners, and bordered surfaces. These are optional suggestions.

The title has a separate italic phrase, the photograph carries the landscape, and the compact planner sits directly after it. Room comparison cards keep the same image height and align their lower details. On narrow screens the introduction, form, cards, and house-details band stack. All UI color, type, spacing, focus, corners, and surfaces consume shared tokens.

The generated landscape is replaceable content, not a palette override. It depicts a fictional property. Room plans are decorative concept illustrations; they are not accurate floor plans or evidence of actual accessibility features.

## Editable content

Shared `Stay01Props` accepts identity and copy through `name`, `eyebrow`, `title`, `titleAccent`, `description`, and `location`. Set `heroSrc`, `heroAlt`, and `imageCredit` to replace the photograph. An empty source uses the core Image fallback.

`rooms` contain unique `id`, `name`, `description`, integer `guests` capacity (1–20), `area`, `bed`, optional `amount`, optional `imageSrc`/`imageAlt`, and optional `href`. Amounts are indicative nightly rates in major currency units; zero is allowed. `currency` and `locale` configure Price. Omit the amount for a host-rate enquiry state. Supply real images to replace concept diagrams. An empty room array produces an honest empty state and disables the planner.

`details` contain `id`, `title`, and `description`; an empty array removes their section and navigation link. Optional `contactHref` adds a real contact destination. All IDs must be unique within their collection and anchor-safe. Replace the fictional `notice` before publishing a real property.

## Date preferences and routing

Arrival/departure use native date Inputs with shared min/max support. `minDate` and `maxDate` are optional ISO dates; the application should supply its own earliest bookable date. There is no server/client clock assumption. `maxNights` defaults to 30. Calendar validation rejects impossible dates, reversed/same-day stays, unsupported guest counts, and out-of-range stays. Nights are calculated in UTC, avoiding daylight-saving day-length errors.

Explore rooms filters the supplied collection by guest capacity. It **does not check date availability, reserve inventory, or calculate a binding quote**. The UI keeps that distinction explicit. Editing a draft after applying preferences announces that the results need updating. Changed room capacity invalidates incompatible applied preferences; Reset clears them.

Use `roomHref(room, request)` to build a destination from the last valid applied request, or use each room's static href. The request has arrival, departure, guests, and nights; it is null before valid preferences are applied. No destination means a sample state, not a fake booking button. The application owns booking/search services, availability, pricing, payments, and server validation.

## Assets and release boundary

The original generated PNG is included in the canonical block assets and schema 2 development bundles. [Binary asset support](binary-assets.md) preserves its exact bytes during source-copy installation. Current public registry 0.1.2 and published CLI 0.3.0 remain schema 1; they cannot install Stay01 yet.

The core audit added native min/max/step forwarding to both framework Inputs. Date helpers, capacity filtering, linked errors, reset/invalidation, replaceable content, schema 2 copying, and old-release installation are covered by automated checks. Browser visual review remains pending because the connected browser/desktop capture is unavailable.
