# Core component development: forms and application depth

Prepared 10 November 2026. Batch 1 is now implemented in development: Fieldset, InputGroup, React Spinner parity, and additive FormField control bindings. These ship in core 1.6.0, design 1.10.0, Vue 1.5.0, and React 0.4.0 with registry 0.3.0. Batch 2 FileUpload and Combobox are implemented in development after 0.3.0; Dropdown/Menu audit is now implemented in development; remaining parity work stays planned. The immediate focus is core components and their composition; recipe expansion remains paused.

## Why this pass

Recent blocks exposed practical gaps that were addressed in core: Checkbox descriptions/errors, Switch form semantics, Pagination, Avatar parity, Stat, and Sparkline. Continue that approach. A new component should remove a repeated product problem, provide useful semantics or behaviour, and remain small enough to compose into several layouts.

The next pass should support account forms, onboarding, product editing, invitations, and checkout details. Each numbered registry block still needs its own deliberate composition. A component showcase or connected workflow is an example, not a numbered block.

## Audit findings

The preparation audit found these Vue components without corresponding React components: AvatarGroup, BarChart, ChartLegend, DonutChart, Dropdown, FileUpload, Kbd, LineChart, MenuItem, MenuSeparator, PageHeader, Spinner, and Stepper. Export presence is only a starting point: audit behaviour before copying an implementation. Existing source is not proof of keyboard, form, or visual readiness.

The component index is incomplete in places: for example it marks Vue Icon unavailable even though the Vue barrel exports it. Reconcile public names, guides, and real framework support during each batch. Installed package declarations remain authoritative for published versions.

FormField supplies label, description, and error markup. It now offers React child-function and Vue scoped-slot control bindings while preserving static children/slots and explicit IDs.

Fieldset and InputGroup are now implemented in both frameworks. Spinner parity has also been completed. FileUpload has a shared contract and Vue implementation; it needs a behaviour audit and React parity rather than another unrelated upload API.

## Batch 1: form structure and compound controls

| Addition | Product purpose | Component boundary |
| --- | --- | --- |
| Fieldset | Related address fields, notification choices, billing details, permissions | Native fieldset/legend, optional help/error, disabled group semantics; children own layout |
| InputGroup | Search with action, currency/unit fields, URL prefixes, password visibility | One control surface with leading/trailing content; the input retains its label, value, constraints, and events |
| Spinner parity | Saving, loading buttons, inline requests | React matches the audited Vue/shared contract; loading announcements belong to the owning action or region |
| FormField composition support | Consistent help/error relationships across all controls | Additive ID/description wiring; preserve manually supplied IDs and current component usage |

### Fieldset design brief

Use a native fieldset and legend. Prepare id, legend, description, error, disabled, and a restrained default/panel presentation. Link the fieldset to its help/error text; do not imply that every child automatically references those IDs. The native disabled behaviour must remain intact, including HTML's first-legend exception. Avoid placing interactive controls inside the legend in examples.

The default should provide clean grouping and spacing without adding another card. An optional panel uses shared card surface, radius, padding, and border roles. The component does not decide column counts, responsive form layout, submission, or validation rules. Compose those through Flex and the application.

### InputGroup design brief

Support leading and trailing content: Vue named slots and React node props, plus the actual control as default content/children. Use a single form surface, coherent focus treatment, and token-driven spacing. Start with one Input per group. Evaluate Select and Textarea separately rather than promising every arbitrary child behaves correctly.

Text adornments such as currency symbols and units need intentional accessible treatment. Decorative adornments should not create redundant announcements; meaningful units should be included in the control's accessible description. Interactive trailing actions remain real buttons with names, keyboard focus, and disabled/loading states. The group itself is not a label and must not create a nested label around controls and buttons.

InputGroup does not own the value, validation, submission, password state, or persistence. Required/disabled/invalid semantics must reach the actual input; a styled wrapper cannot substitute for them. Prepare examples that make this distinction clear. Check focus when moving from the input to a trailing action, and prevent double borders, duplicate shadows, or a second focus ring from competing with the shared surface.

### Batch 1 delivery

Implemented in both framework barrels, with a searchable form-composition core preview in the playgrounds and public In progress gallery. It demonstrates suggested addresses, currency adornments, help/error binding, a disabled notification group, native form values, and a guarded pending/failure/retry action. No numbered block was added. Form borders share the form-border-width role so recipes retain their control treatment. Spinner stops rotating under reduced motion and supports decorative use.

See [Fieldset](components/fieldset.md), [InputGroup](components/input-group.md), [FormField](components/form-field.md), and [Spinner](components/spinner.md). Browser visual/native interaction review remains pending when no connection is available.

### Completion evidence

- Vue and React implement the same shared contracts and useful states.
- Native form submission, labels, help/errors, disabled groups, and action focus remain correct.
- Radius, density, surface, palette, and recipe choices continue to work independently.
- Larger recipe typography must fit intrinsically or cause an intentional layout wrap; do not rely only on viewport breakpoints or shrink the recipe to hide collisions. Review short/long labels and minimum/maximum display values.
- A searchable core-component preview shows plain, panel/grouped, invalid, disabled, and pending examples.
- Examples use real local state and actions; they are not additional registry blocks.
- Guides include small Vue/React examples and clearly distinguish development from published APIs.

## Batch 2: files and searchable selection

### FileUpload audit and parity

Review the existing contract and Vue implementation before finalizing the cross-framework API. Define selected-file ownership, selecting the same file again, single/multiple replacement, duplicate identity, removal, size/type rejection, disabled behaviour, native picker access, and drag/drop fallback. Decide whether native form submission is supported and document it accurately.

Keep selection separate from transfer. Local file selection must not display invented upload progress or completion. Server uploading, cancellation, retry, storage, and authorization belong to an application-supplied integration. Local checks improve feedback; they do not establish server-side file safety.

The FileUpload audit is now implemented in development after 0.3.0. Both frameworks support controlled/local selection, shared type/size/duplicate checks for picker and drop, rejected single-file replacement recovery, disabled guards, native labelling/focus, and dropzone/compact preset variants. The earlier Vue update:files event is preserved. Selected files are app state; native form submission is deliberately not claimed. A dedicated In progress core preview and guide cover these boundaries. See [FileUpload](components/file-upload.md). Combobox is also implemented below in this batch.

### Combobox

Add searchable single selection for customers, assignees, courses, and products. Start with a controlled value and stable option identities, clear keyboard navigation, linked listbox/options, disabled options, no results, loading, and optional clear behaviour. Separate the query from the selected value. The application owns remote search and stale-response handling.

Do not combine multi-selection, free-form tags, async creation, and command navigation into the first version. Evaluate those after the single-selection interaction is sound. Use the accessibility references applicable at implementation time and verify actual keyboard behaviour.

The first Combobox is now implemented in development after 0.3.0, with Vue/React parity and shared matching/navigation helpers. Selection and query are independent; native form values use the committed option ID. Keyboard exploration, disabled choices, clear, loading/error/empty results, and stale active-reference removal are covered. Remote fetching and result correlation remain application-owned. The In progress core preview includes a fictional async adapter and recovery controls. Inline popup positioning remains bounded; portal/collision handling and browser/native review are future work. See [Combobox](components/combobox.md).

## Batch 3: application interaction parity

Audit Dropdown/Menu items and separators, then Stepper, before creating more action-heavy application blocks. Distinguish menu actions from navigation links. Confirm dismissal, focus restoration, keyboard behaviour, disabled actions, and controlled state. A step indicator does not validate a form or silently advance a workflow.

Dropdown audit and React parity are now implemented in development after 0.3.0. It connects an actual button to the existing Menu, with controlled/local state, keyboard entry, Escape/selection focus return, outside/Tab dismissal, and cleanup. Supporting Menu/MenuItem/MenuSeparator parity retains their existing variants and adds shared roving navigation, Home/End, typeahead, guarded disabled links/actions, and appropriate callback semantics. This is a core preview, not a new menu system or block. Inline placement remains bounded; the shared portal/collision layer and browser/native review are future work. See [Dropdown](components/dropdown.md).

Evaluate PageHeader, AvatarGroup, Kbd, and remaining chart parity as concrete products require them. A full chart needs appropriate data access, scales, tooltips, responsiveness, theme updates, and a readable alternative. Do not use a decorative sparkline to imply unsupported analytical behaviour.

Date-range selection, rich text, command search, and advanced table/server workflows remain later work. Inline single-date Calendar is now implemented for Booking01; it does not imply a complete date-picker/range system. These larger capabilities require dedicated interaction designs and integration boundaries.

## How each batch ships

1. Record the product jobs, shared API, semantic structure, state ownership, and token roles.
2. Implement both frameworks and meaningful shared logic before adding showcase compositions.
3. Verify relevant behaviour and native semantics, then typechecks and production builds.
4. Review desktop/mobile, keyboard, light/dark, density, radius, and surface combinations. Record when browser review cannot be performed; build success is not visual approval.
5. Add guides and discoverable playground entries. Keep components, examples, recipes, and registry blocks distinct.
6. Prepare a coordinated package release only after the batch is ready. Give changed packages new versions and verify clean consumers. Preserve immutable registry 0.1.2/0.2.0 and their existing package metadata.

Batch 1 and the Calendar/Stepper follow-ups are included in published registry 0.3.0 and its coordinated package versions. Future batches need their own prepared release. Use the existing [publishing workflow](registry/publishing-commands.md) only after a newly prepared, verified release; the old archives do not contain future component work.

## Product-driven follow-up: Checkout01

On 11 November 2026 the owner returned the focus to standalone blocks. Checkout01 uses the new form foundations and prompted React Stepper parity and descriptive Radio support. This implements the Stepper portion of batch 3 in a concrete product context; FileUpload and Combobox have since been implemented in development; the remaining interaction audits stay planned. See [Checkout01](registry/checkout-01.md).

Booking01 now adds inline Calendar in both frameworks: shared real-date arithmetic, six-week grid, controlled selection, explicit availability/bounds, locale/week start, and day/week/month/year keyboard navigation. Booking state, service requests, timezone conversion, and confirmation remain above the core component. No new recipe was added. See [Booking01](registry/booking-01.md) and [Calendar](components/calendar.md).

## Application01 audit (development after 0.3.0)

AvatarGroup gains a shared member contract, bounded overlap, aggregate accessible naming, overflow and React parity while preserving Vue slots. FileUpload gains maxFiles and count rejection without deleting existing app-owned files. MenuItem forwards native download for actual public brief files. Application01 exercises these alongside Combobox, Fieldset and FormField; submission remains application-owned.
