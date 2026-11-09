# Component status

Every public component is labeled with one of four stability levels. Check a component's own page for its current label before depending on its API in production.

| Label | Meaning |
| --- | --- |
| `experimental` | API may change without a deprecation period. Avoid in production. |
| `beta` | API is close to final; breaking changes are called out in the changelog and given a deprecation period. |
| `stable` | API is frozen. Breaking changes require a major version and a migration guide. |
| `deprecated` | Scheduled for removal. A replacement is documented; migrate before the next major version. |

See [contributing](contributing.md) for how a component moves between these labels.
