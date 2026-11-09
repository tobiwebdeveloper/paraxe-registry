# Learning and pricing layouts

Chat01 and Pricing01 are experimental, editable registry layouts for Vue and React. Both use Flex and shared components. They follow the same independent recipe, palette, font, density, radius, and surface axes as the commerce blocks.

## Design direction

The user supplied a Medly pricing screenshot: centered introduction, three comparable columns, prominent prices, feature dividers, highlighted one-off plans, and actions anchored at the bottom. Pricing01 follows that hierarchy without copying brand assets, fixing lime in CSS, or claiming the sample plans are a live offer. Formatting follows the shared Price component, including currency precision.

The educational direction also draws on the learning context of [Medly](https://www.medlyai.com/us) and [Knowunity's study chat](https://knowunity.co.uk/ai/chat). Their official pages describe tutoring, practice, and study conversations. The new Paraxe recipe is an interpretation, not a verified visual reproduction of either product.

## Pricing01

A centered heading and three equal-width cards on desktop; wrapping columns on tablets and a stack on mobile. Each card has a badge band, plan identity, display price/cadence, description, feature list, and bottom action. Featured cards use the paired brand/foreground tokens. Normal cards retain core Card treatment and preset corners. Feature checks are decorative; list text carries their meaning.

Pass `plans` with unique `id`, `name`, major-unit `amount`, `cadence`, `description`, and `features`. Optional fields: `badge`, `featured`, `actionLabel`, and `href`. `currency` and `locale` must be explicit and consistent between server and client. Negative/nonfinite amounts and duplicate IDs are rejected. Empty plans remove all sample cards.

Real `href` values enable navigation; absent destinations render disabled buttons. No checkout, provider, subscription, payment-link service, or refund policy is bundled. Replace the illustrative plan terms and `note` before production. `helperHref` and `helperLabel` can expose an app-owned alternative-payment route.

Other text props: `eyebrow`, `title`, and `description`.

## Chat01

A study context column beside a framed conversation workspace. Sender labels, role-based message surfaces, bounded scrolling, starter prompts, a labelled multiline composer, and pending/error states form the layout. On smaller screens the context stacks above the conversation.

`messages` is application-owned: an array of unique `id`, `role` (user or assistant), and plain-text `content`. The block escapes content and does not interpret HTML or Markdown. Starter `prompts` populate the draft. `sendMessage(text)` receives trimmed text. Add messages and responses in your application; the block does not invent assistant replies or keep a second conversation store.

Without a send handler, submission is disabled and a preview notice explains why. Empty or whitespace-only drafts cannot submit. A pending submission blocks duplicates and disables editing. Success clears the draft; errors preserve it and expose a generic alert without leaking backend details. Input is limited to 4000 characters. The conversation uses a labelled live log; closed-page history is not persisted by this block. No AI SDK or network transport is bundled.

Replace `title`, `description`, `contextTitle`, `contextDescription`, `prompts`, and the `labels` map to suit the product. Subject-specific teaching logic, streaming, attachment handling, moderation, persistence, and authentication belong in application integrations or future dedicated controls.

## Core improvements

Textarea now shares `rows`, `placeholder`, `required`, `describedBy`, and invalid-state semantics across frameworks. React uses the native change event for controlled updates. Price gains `size="display"`, backed by a shared semantic typography role. Conversation surfaces and bubble radius are shared tokens; blocks do not redefine them locally.

## Preview

- Educational chat using your saved colours: `?preview=chat-01&recipe=educational`
- Clean pricing using your saved colours: `?preview=pricing-01&recipe=clean`
- Educational pricing in dark mode: `?preview=pricing-01&profile=educational&theme=dark`
- Preserve project axes while changing treatment: `?preview=pricing-01&recipe=educational`

Profiles affect only the current preview. They never modify saved project configuration. Both layouts are registered in [the published registry index](https://tobiwebdeveloper.github.io/paraxe-registry/r/v0.1.2/index.json).

## Validation

Recipe matrix tests cover seven recipes, three accents, two radii, and both modes, including featured price foreground/background pairing. Both framework entries have SSR coverage for editable content, empty states, safe text, and disabled actions. A Vue component-renderer test exercises asynchronous sending and failed/successful drafts. Registry token checks enforce shared styling roles. Browser-based visual review remains pending because no browser connection was available during implementation.

## Chat colour mapping

Conversation backgrounds and text use separate shared roles: `--chat-assistant-surface`, `--chat-assistant-text`, `--chat-user-surface`, and `--chat-user-text`. User bubbles follow the muted accent in every recipe, including Clean. Default demo links select a recipe only, preserving saved colours and other preset axes. Explicit `profile` URLs intentionally load the whole suggested profile, including its accent; use `recipe` when adjusting an existing project. The Educational button treatment is unchanged.
