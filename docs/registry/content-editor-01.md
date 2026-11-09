# ContentEditor01 and the content workspace

The product direction now prioritizes depth in common application components and forms. ContentEditor01 is an embeddable writing-form layout. The content workspace is a composition **example**, not another registry block: it connects AppShell, Sidebar, Navbar, Breadcrumbs, Table, and the editor using ordinary application state.

Try `?preview=content-workspace&profile=swiss&theme=light` in either playground, or `?preview=content-editor-01&profile=swiss&theme=light` for the editor on its own. Neither entry introduces a recipe. ContentEditor01 is included in registry 0.2.0; the connected workspace is a separate composition example. Check [release status](../reference/release-status.md) during rollout.

## Editor contract

ContentEditor01 renders a section that can sit inside an AppShell main region or a page container. Its writing column groups title, URL slug, summary, and body. A side column holds status/category settings and a live summary card; the action bar carries save, preview, and back actions. The layout stacks on narrow screens and consumes shared tokens throughout.

Required modelValue contains title, slug, summary, body, category, status, and optional id. Status is draft, review, or published. categories defaults to Guides/Stories/Updates. Optional errors is a field-to-message map; pending disables editing/actions; dirty drives the change indicator; message provides status feedback. showBack and allowPreview expose their actions.

Vue emits update:modelValue with a copied draft, submit with a copied draft, cancel, and preview. React uses onModelValueChange, onSubmit, onCancel, and onPreview. The parent owns validation, persistence, permission checks, workflow transitions, and dirty navigation. The block supplies linked field errors, native constraints, and pending presentation. Use the shared prepareContentDraft helper for the demonstrated rules, or supply application-specific rules.

The body is plain text, not a rich-text engine. There is no pretend formatting toolbar. Connect an editor engine deliberately if the product needs one, and define a matching content/preview contract.

## Connected example

The workspace has searchable, status/category-filtered content; native table sort/selection controls; selected-record editing and JSON export; new/edit states; live preview; and local saves that update the content library and counts. Filters clear selection so hidden rows are never exported accidentally.

New draft titles suggest a slug until it is customized. Existing saved URLs remain stable when a title changes. Duplicate slugs, invalid statuses/categories, length limits, and non-draft entries without body text are rejected. Submitted work is snapshotted, repeated saves are locked, failed saves preserve the draft, and invalid save responses do not overwrite it.

Navigation away from dirty work requires an explicit stay/discard choice. The requested destination, including its filter, is preserved. Starting a save clears a pending navigation prompt and blocks navigation until it finishes. Preview keeps the same draft. All preview text is framework-escaped.

The example stores data **only in the current tab's memory**. Reloading resets the fixtures. Published status is local metadata in this example, not a public publishing service. An optional persistence callback in createContentWorkspace demonstrates a server boundary; production must add authorization, revision/conflict handling, idempotency where needed, and server validation. No browser storage or remote endpoint is silently added.

## Core improvements

- React AppShell now matches Vue's composition contract; both have named main/navigation targets and a mobile disclosure.
- React Sidebar/SidebarItem/Breadcrumbs now honor their preset variants, and navigation actions use native buttons.
- Table uses native sort buttons and named checkboxes, supports controlled selectedRows within supplied rows, preserves stable identity, and exposes caption/empty/loading content. Selectable rows require unique stable keys. Cross-page selection belongs to the application.
- Input forwards minlength/maxlength/pattern. Textarea forwards minlength and invalid. Input/Select/Textarea give invalid fields the error appearance; invalid/error takes precedence over success.

Tests cover core rendering in both frameworks, table interactions, the connected Vue client flow, validation, dirty navigation, saving/rejection, and recipe independence. Builds/typechecks cover both playgrounds. Browser visual, font, download, and actual keyboard review remain pending while browser capture is unavailable.
