# Paraxe development backlog

## Monochrome button and brand-foreground treatment

Status: deferred at the owner's request on 9 November 2026. Continue recipe/block development; do not change the successful chromatic palettes as part of this investigation.

Owner observation: monochrome buttons and brand text can look white/grey rather than the intended crisp black/white treatment. Treat monochrome as a deliberate exception, not just another chromatic hue.

Investigate `brand-primary`, `text-on-brand`, button backgrounds/borders, muted foregrounds, and hover/active/disabled/loading states in both light and dark modes. Distinguish deliberately disabled controls from enabled actions with insufficient visual separation. Check featured surfaces as well as buttons and each recipe's borders/shadows.

Acceptance: enabled monochrome actions have clear paired foreground/background roles; secondary/text controls remain readable; intentional disabled/muted states are distinguishable; semantic and chart colours stay independent; chromatic palettes retain their current values and treatment. Verify actual browser rendering and contrast, alongside token/recipe regression tests. This item records feedback, not a confirmed diagnosis or an implementation.

## Common application depth

Prioritize reusable settings/account forms, product-management fields, and richer data workflows. Continue auditing shared Checkbox, Pagination, overlay and table contracts before composing them. Cross-page table selection, server sorting/pagination, conflict-aware persistence, real rich-text editing, and browser/keyboard review remain future integrations, not claims of the local content-workspace demo. Further recipe expansion is paused.

The next component batches and their acceptance criteria are prepared in the [core component development plan](core-component-roadmap.md): form structure/compound inputs first, then file selection and searchable selection, followed by application interaction parity. These are planned additions, not published exports.
