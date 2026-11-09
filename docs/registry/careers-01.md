# Careers01

A recruiting layout for company websites: typographic masthead, oversized open-role count, split mission and job board, grouped role articles, principles, and hiring steps. Flex handles the page composition; filters stack on narrow screens. Swiss is a suggested pairing, not a dependency.

Development preview: `?preview=careers-01&profile=swiss` in either playground. This block is not part of registry 0.1.2 yet.

## Replace the content

Both frameworks accept `company`, `logoSrc`, `companyHref`, `eyebrow`, `title`, `description`, `introTitle`, `introDescription`, `roles`, `principles`, `steps`, and `notice`. Titles support a newline. Logos and all text are replaceable. Empty arrays remove sample content.

Each role has `id`, `title`, `department`, `location`, `commitment`, `description`, and optional `href`. Supply real application destinations to turn titles into native links. Without a destination, a role is explicitly marked as a sample. IDs must be unique within each collection and contain only letters, digits, underscores, or hyphens, starting with a letter or digit.

Principles and steps each have `id`, `title`, and `description`. Replace the fictional hiring notice before publishing a real company's page.

## Filtering and application ownership

Search matches all entered words across role text. Department and location narrow the results together. Options derive from current data; selections whose options disappear recover to all. A clear action restores the board after an empty search. The page does not send applications or invent an applicant-tracking service: route links into the application's hiring flow.

Typography, accent, borders, spacing, density, and surfaces consume system tokens. Local `--careers01-*` aliases provide layout roles. Palette and preset axes remain independently editable.
