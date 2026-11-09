# Contributing

Update the implementation and core contract first. Then regenerate documentation with `pnpm docs:generate` and run `pnpm docs:check` plus the relevant package type checks. Documentation is generated from public barrel exports and core contract files to reduce drift; add explanatory prose in the generator when a component needs framework-specific context.
