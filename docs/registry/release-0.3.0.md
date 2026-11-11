# Published release 0.3.0 — 11 November 2026

This coordinated update includes all work since registry 0.2.0: 24 experimental layouts in Vue and React, with 48 source bundles and the existing nine recipes. All five packages are published; their archive integrity matches the verified release. See [release status](../reference/release-status.md).

| Package | Published version | Previous published version |
| --- | --- | --- |
| @paraxe/core | 1.6.0 | 1.5.0 |
| @paraxe/design | 1.10.0 | 1.9.0 |
| @paraxe/vue | 1.5.0 | 1.4.0 |
| @paraxe/react | 0.4.0 | 0.3.0 |
| @paraxe/cli | 0.5.0 | 0.4.0 |

## New layouts and core work

The six new layouts are [Settings01](settings-01.md), [Orders01](orders-01.md), [Course01](course-01.md), [Dashboard01](dashboard-01.md), [Checkout01](checkout-01.md), and [Booking01](booking-01.md). All remain editable source, with application-owned data/services and independent preset axes.

Core additions include Calendar, Fieldset, and InputGroup in both frameworks; React parity for Spinner, Stepper, Stat, and Sparkline; shared pagination/date/geometry/progress models; improved Avatar recovery/parity; linked FormField control bindings; and descriptive Checkbox, Radio, and Switch semantics. Shared design CSS includes their token-driven surfaces and sizing. CLI 0.5.0 pins registry 0.3.0 and includes the new form variant configuration.

The existing eighteen layouts and nine recipes are included. The update also carries the revised Dashboard composition, intrinsic metric/chart sizing, and the latest form/layout refinements. Recipe expansion is paused. Backend persistence, payments, reservations, authorization, and calendar-provider integrations remain application responsibilities.

## Publish npm

Run these in a PowerShell terminal, after the prepared archives have passed verification:

```powershell
Set-Location "C:\Users\tobio\paraxe"
& .\releases\npm\publish.ps1 -DryRun
& .\releases\npm\publish.ps1
```

Run the script file; do not paste its contents. It publishes the exact verified archives through pnpm to npm, in core/design/Vue/React/CLI order. Authentication and any two-factor challenge stay in the terminal. A retry skips versions only when their published integrity matches the prepared archive. Never rebuild changed contents under the same version after publication.

## Registry sequencing

Registry 0.3.0 uses schema 2 and the versioned path `r/v0.3.0/index.json`. CLI 0.5.0 uses that path by default. Registry 0.1.2 and 0.2.0 stay unchanged; their older CLIs keep their existing defaults.

After clean-consumer verification, `pnpm registry:stage` publishes only the new immutable versioned files. It leaves the existing gallery, documentation, and package-install instructions intact, so it does not advertise unpublished npm versions. This puts the new CLI's destination online before npm publication. Staging verifies the archive manifest, consumer verification record, registry index, every release-file hash, and unchanged existing destination files.

After all five new npm versions are published and their integrity checked, update publishedPackages in registry/release.json, promote the release status/guides, then run `pnpm registry:release`, `pnpm registry:preview`, and `pnpm registry:deploy`. The deployment script checks npm availability before promoting the full site. Regenerating the same immutable release is allowed only when its bytes are identical. The maintainer only needs the npm commands above; the registry promotion is handled separately.

## Verification evidence

Preparation writes five `.tgz` files and release-manifest.json under releases/npm. release:verify installs those archives outside the monorepo, copies and checks all 48 bundles using the packed CLI, checks all nine recipe exports, builds both framework consumers, and checks their component/block declarations. It writes verification.json only after success. The publishing helper requires that record and matching archive hashes. Previous 0.2.0 manifest/verification records are retained under releases/npm-history/registry-0.2.0; old tarballs remain available locally.

Automated tests, typechecks, integrity checks, and builds do not replace visual/native keyboard or assistive-technology review. Browser review remains pending when the review connection is unavailable; experimental status is preserved.
