# Published release and development status

Verified against npm version metadata and the exact prepared archive integrity on 11 November 2026.

| Package | Published release |
| --- | --- |
| @paraxe/core | 1.6.0 |
| @paraxe/design | 1.10.0 |
| @paraxe/vue | 1.5.0 |
| @paraxe/react | 0.4.0 |
| @paraxe/cli | 0.5.0 |

Registry **0.3.0** contains **24 experimental layouts / 48 framework bundles**, with schema 2 text/binary assets. CLI 0.5.0 pins its immutable index. Nine recipes are available: Default, Editorial, Educational, Clean, Swiss, Brutalist, Studio, Cinematic, and Organic. Palette, fonts, density, radius, surfaces, and component variants remain independent.

Sources: [core](https://www.npmjs.com/package/@paraxe/core/v/1.6.0), [design](https://www.npmjs.com/package/@paraxe/design/v/1.10.0), [Vue](https://www.npmjs.com/package/@paraxe/vue/v/1.5.0), [React](https://www.npmjs.com/package/@paraxe/react/v/0.4.0), [CLI](https://www.npmjs.com/package/@paraxe/cli/v/0.5.0), and the [registry index](https://tobiwebdeveloper.github.io/paraxe-registry/r/v0.3.0/index.json).

## Included in 0.3.0

The six additions since 0.2.0 are [Settings01](../registry/settings-01.md), [Orders01](../registry/orders-01.md), [Course01](../registry/course-01.md), [Dashboard01](../registry/dashboard-01.md), [Checkout01](../registry/checkout-01.md), and [Booking01](../registry/booking-01.md). They are installable layouts, rather than In progress previews. All eighteen earlier layouts are retained. Connected shop/content demos remain examples, not extra numbered blocks.

Core additions include [Calendar](../components/calendar.md), [Fieldset](../components/fieldset.md), [InputGroup](../components/input-group.md), React parity for Spinner/Stepper/Stat/Sparkline, shared date/pagination/progress/geometry helpers, improved Avatar recovery/parity, FormField control bindings, and descriptive Checkbox/Radio/Switch semantics. The associated design roles and CLI variant support ship together. Booking confirmation, checkout pricing/payments, persistence, authentication, and external services remain application-owned.

## Verification and compatibility

All five published archive SHA-512 values match their prepared archives. Clean-consumer verification installed all five archives outside the monorepo, copied and checked every one of the 48 bundles with the packed CLI, checked all nine recipe exports, built both framework consumers, and checked their component/block declarations. Evidence is retained under releases/npm. See [release 0.3.0](../registry/release-0.3.0.md) and [publishing commands](../registry/publishing-commands.md).

Registry **0.2.0** (18 layouts / 36 bundles) and **0.1.2** (9 layouts / 18 bundles) remain unchanged. CLI 0.4.0 keeps its registry 0.2.0 default; CLI 0.3.0 keeps registry 0.1.2. Installing new 0.3.0 blocks requires the package versions above. Installed declarations remain authoritative for applications on older versions.

[Current contracts](current-contracts.md) describe workspace source. Future development can move beyond this published baseline; read each feature's release note rather than assuming every workspace change is in npm. All blocks remain experimental. Browser visual/native keyboard and assistive-technology review remain pending where review connections are unavailable; successful builds are not visual approval.

## Development after 0.3.0

The FileUpload audit and React parity are newer workspace source: controlled selection, consistent picker/drop type and size validation, duplicate feedback, guarded removal, native focus/labels, token-driven dropzone/compact surfaces, and preset/provider variant support. They appear under In progress as a core-component preview. Published Vue 1.5.0 retains the earlier implementation; React 0.4.0 does not export FileUpload. No published archive or immutable bundle has been changed. See [FileUpload](../components/file-upload.md).

Combobox is also development after 0.3.0 in both frameworks: searchable single selection, controlled option ID/query, disabled choices, native committed-ID form values, required validity, keyboard exploration/commit/cancel, and app-owned loading/error/search results. The public In progress preview includes local and fictional remote examples. It is not in the published packages above. See [Combobox](../components/combobox.md).

Dropdown now has React parity and an audited native-button/open/dismiss/focus contract in development after 0.3.0. It uses the existing Menu/MenuItem/MenuSeparator composition; Menu retains its variants while gaining shared keyboard handling and React parity. Disabled links are inert, selection can keep the popup open intentionally, and outside/Tab dismissal preserves destination focus. Published Vue/React archives retain their earlier implementations. See [Dropdown](../components/dropdown.md).

[Application01](../registry/application-01.md), data-driven [AvatarGroup](../components/avatar-group.md)/React parity, FileUpload.maxFiles and MenuItem.download are development after registry 0.3.0. Preview visibility does not imply npm or immutable registry availability. Published archive versions and hashes are unchanged.

The SVG Icon implementation, audited Tooltip and revised [Footer01](../registry/footer-01.md) are development after registry 0.3.0. The current npm archives and versioned Footer01 bundle retain their earlier implementations.

The [overlay surface audit](../components/overlay-surfaces.md) is development after registry 0.3.0: new shared surface props, Popover local/controlled ownership, real trigger semantics, modal stack/focus/inert/scroll handling and built-in close controls. Published archives retain the earlier versions. A coordinated package release is still required. The existing iconLibrary preset setting remains metadata until the planned runtime adapters are implemented.
