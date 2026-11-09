# Block quality and the 01 layouts

A block is a reusable page or section layout. Combining a few components is not enough. Each numbered block must justify its existence through structure: clear alignment, proportions, hierarchy, content rhythm, responsive behaviour, and a distinct composition that survives real content.

## Audit: Footer01 and FAQ01

The first versions did not reach the quality of the commerce collection and product page. The main problem was composition: uncontained rows, shallow text hierarchy, no strong section framing, and too little visual anchoring. Flex itself was adequate. Replacing Flex or adding more decoration would not resolve those issues.

There were also core gaps. FAQ01 bypassed Accordion entirely. The existing Accordion had no built-in expand indicator or surface variants, used item IDs without instance scoping, and lacked heading semantics around its triggers. React Heading did not forward IDs and accessibility attributes. These are reusable foundation concerns, now fixed in the core rather than patched only inside the block.

## Changes

Accordion now supports divided, bordered, and plain treatments; shared typography, spacing, border, surface, and radius roles; a plus/minus indicator; semantic trigger headings; instance-scoped trigger/panel IDs; and preset variant resolution. Single-open initial state respects the `multiple` option. Behaviour checks cover switching, collapsing, disabled activation, multiple selection, and non-collapsible state. Repeated-instance IDs are checked during server rendering.

FAQ01 uses a contained split layout. Its introduction, support card, numbered question rail, row dividers, count, and initial expanded answer form a deliberate hierarchy. The core Accordion owns the disclosure treatment. Footer01 uses a masthead, editorial contact column, divided navigation columns, large brand signature, and utility band. Both stack on smaller screens and use shared token roles.

## Rules for future blocks

- Start with the existing core. Audit its behaviour, semantics, styling hooks, and framework parity before adding block-specific UI.
- Define the layout's purpose and geometry before choosing sample content. Explain what makes 02 structurally different from 01.
- Give each section clear boundaries, aligned edges, deliberate type scale, and a readable content measure. Whitespace needs a structural purpose.
- Use tokens and component variants for visual treatment. Blocks may define local aliases and layout rules; they must not freeze a palette, font, density, or radius.
- Make sample content and destinations replaceable. Handle empty and long content without leaving fake actions or collapsing the layout.
- Check behaviour and semantics in both frameworks, then inspect the desktop and mobile render in light/dark modes and contrasting recipes. Passing a build alone is not visual approval.

## Verification limits

The implementation is covered by framework typechecks, component behaviour and SSR tests, registry token checks, and production builds. Interactive browser visual review was unavailable during this pass; pixel alignment, actual font loading, and small-screen appearance still require visual verification.

## Structural decisions

Discuss the direction of future recipes and block layouts with the user before building them. Routine token wiring, colour corrections, behaviour fixes, and explicitly requested playground tooling can continue within the agreed scope.

Composition demos and routing examples are not registry blocks. Every numbered block must contribute a distinct, deliberate layout. The connected shop remains an example; Portal01 is a new member-home layout. Recipe variety should support these product jobs while preserving editable preset axes.

Use the [block-and-recipe formula](../block-and-recipe-formula.md) for new additions. Typography/control proportions and the product job are explicit design inputs.
