# Website foundations: Footer01 and FAQ01

These numbered registry entries are editable layouts for Vue and React. Both use Flex composition and shared visual roles. See the [quality audit and future block standard](block-quality.md).

## Footer01

A contained editorial footer: masthead, contact introduction, divided navigation, oversized brand signature, and legal band. It stacks on smaller screens. Pass `brand`, `eyebrow`, `title`, `description`, `edition`, `copyright`, `contactLabel`, `contactHref`, `groups`, and `legalLinks`. Groups contain `title` and `links` with `label` and `href`. Legal links use the same link shape. Replace sample routes with application destinations. Empty `groups` or `legalLinks` remove their sample links; an empty `contactHref` hides the contact action.

## FAQ01

A contained split layout: editorial introduction and support card on the left; question count and numbered accordion rows on the right. The first answer opens initially. Questions use shared Accordion/AccordionItem controls, heading semantics, instance-scoped IDs, and plus/minus indicators. Palette, typography, row density, surfaces, and corners remain preset-owned.

Pass `eyebrow`, `title`, `description`, `items` containing `question` and `answer`, and optional support copy using `supportTitle`, `supportDescription`, `supportLabel`, and `supportHref`. An empty `supportHref` hides the support card. Answers are framework-escaped plain text. Empty items produce no sample questions. Default opening is initial state, not a controlled selection API.

## Preview and composition

Hero01 is contained by default, aligned to the shared container width and page gutters. Pass `width="full"` to fill its parent's available width; a constrained parent still constrains it. This width option is a development API and is not in registry 0.1.2. Both modes retain the same recipe and token behavior. Compare `?preview=hero-01` with `?preview=hero-01&heroWidth=full` in either playground.

In either playground: `?preview=footer-01`, `?preview=faq-01`, or `?preview=website-01&recipe=editorial`. The website composition uses canonical Navbar01, Hero01, FAQ01, and Footer01 entries. It is a preview, not a production router.

Recipes and setup suggestions are documented in [Component recipes](../foundations/recipes.md). Published source and framework file maps live in [the published registry index](https://tobiwebdeveloper.github.io/paraxe-registry/r/v0.1.2/index.json).

## Next expansion

Cart and order summaries, collection features, image-led stories, contact forms, and richer product purchasing. New numbered variants should introduce a purposeful composition rather than a copy change. Commerce state and submission handlers remain application-owned.
