# Dashboard01

A decision-first project workspace: a performance overview with a dominant delivery figure and scoped reporting history, three focused priorities, a full-width project register, a horizontal handover strip, activity, and ownership. Swiss is the suggested recipe; palette, font, density, radius, and surfaces remain independently configurable. The layout uses Flex and shared core controls, with zero-specificity resets so spacing classes retain their margins.

Try `?preview=dashboard-01&profile=swiss&theme=light` in either playground. Dashboard01 appears under **In progress**, after immutable registry 0.2.0. Its Stat and Checkbox improvements require matching development packages until the next coordinated release; the live preview does not make it installable from 0.2.0.

## Supply a workspace

Import the named React Dashboard01 entry or default Vue entry. Pass a DashboardSnapshot through snapshot. title, description, and locale change the introduction and date formatting. Omitting snapshot uses explicit fictional sample data; supply empty projects, tasks, and activity arrays for a real empty workspace.

A snapshot has id, organization, asOf (timestamp with timezone), currentMemberId, members, projects, tasks, and activity. Members have id, name, role, optional portrait src. Projects have id, code, title, client, summary, ownerId, status, completed and total deliverable counts, date-only due, optional href. Status is on-track, at-risk, blocked, or complete. Tasks have id, title, projectId, optional assigneeId, date-only due, high/normal priority, and done. Activity has id, action, at, and optional actorId/projectId.

Validation copies nested records and checks identities, references, real calendar dates, safe integer counts, completed status, and activity no later than the snapshot. Destinations accept relative paths or HTTPS. Image sources and authorized data access belong to the application.

## Truthful summaries

Whole workspace includes all projects. My work includes projects owned by the current member or containing tasks assigned to them; its priorities contain only tasks assigned to that member. Needs attention includes at-risk, blocked, and overdue unfinished projects. Active excludes complete projects. Due in the next 7 days includes today through seven days after the UTC snapshot day, excluding overdue work. Work completed divides the sum of supplied completed deliverables by the sum of totals.

The health bar is a categorical distribution with textual counts. Ownership counts active projects, rather than claiming capacity. Deadlines show the earliest three unfinished projects, including overdue ones. Activity shows the latest five relevant events. Dates use the supplied locale and explicitly stated UTC timezone. No live analytics or comparison deltas are implied.

Search matches project code, title, client, and owner; search and health filters affect the table only. Summaries continue to describe the selected workspace scope. Core Table sorts all matching rows, without pagination. Empty workspaces and filtered no-results have distinct states.

## Connect actions

updateTask(id, done) may return a promise. The application persists changes and replaces snapshot after success. The block does not optimistically change tasks or infer project delivery from a partial priority list. Pending changes guard duplicate operations. Rejection leaves supplied state unchanged and links the announced error to its checkbox. Workspace replacement and unmount invalidate stale results. A successful request without a replacement snapshot leaves supplied task state visible.

openProject(project) receives a copy and may return a promise; it takes precedence over href. Without a callback, href provides native navigation. Without either, the title stays plain text. Optional createProject and refresh callbacks expose buttons only when connected; their parent owns async lifecycle and loading/error props. loading and error replace the overview so old people/project details are not displayed. retry is optional. These UI states do not implement permissions or application-wide route guards.

The root is a labelled section, suitable inside an AppShell main landmark. Connected application examples remain separate from numbered blocks.

## Preview and core improvements

Both previews include an application-owned project brief, simulated task saving, a failure/retry toggle, and ready/loading/error/empty states. Changes remain in tab memory. The sample service treats each priority as one deliverable and updates its sample snapshot after success; that demo rule is not part of the block.

Stat is now exported in React alongside Vue with shared label/value/change/trend/variant behaviour. Its surface uses card padding, border, background, shadow, and radius roles. Checkbox adds native id, labelledBy, describedBy, and invalid support in both frameworks for richer task rows and linked form errors.

Checks cover derived scopes/totals, validation, both framework renders, linked descriptions, pending and stale-request guards, failure/retry, and preview updates. Browser visual review remains pending when no connected browser is available.


## Composition and history

The overview and priorities share one upper row. Priorities initially show the first three due items; View all expands the remaining work, and Show completed expands the list so completed items remain discoverable. The full-width project register has its own health strip, filters, and sortable columns. Handovers form a shared horizontal strip beneath it. Team activity and ownership have quieter supporting roles. The layout uses density-aware padding and a deliberate type scale rather than equal-weight cards or a long rail competing with a narrow table. Small screens stack these regions and retain table scrolling.

Optional history contains dated reporting points: each has date and projects, whose records contain projectId, completed, and total. Every date must cover all snapshot projects with valid counts, so workspace scopes compare equivalent records. Dates must be unique, real, and no later than asOf. Each scope derives its own historical completion ratio from those records; table search does not change it. Scope totals can change between reporting dates, so the chart explicitly labels completed / total scope rather than claiming velocity. A textual reporting table exposes the underlying dates and counts. Without at least two reports or without projects, the chart is replaced by an explanatory state. There are no inferred trends from one snapshot.

Core Sparkline now has React parity, shared finite-value geometry, optional min/max scale bounds, and decorative/named SVG semantics. This block fixes the scale to 0-100% and uses the brand token. Straight sample segments avoid interpolation overshoot; the core remains useful independently from Dashboard01. The original fictional sample service supplies six explicit weekly observations and updates the latest report when a sample task is saved.
