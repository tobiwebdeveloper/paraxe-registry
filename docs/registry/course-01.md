# Course01

A course overview with a substantial learning plan: replaceable cover artwork, outcomes, searchable module disclosures, lesson states and durations, a progress/continue-learning rail, educator, and study resources. Educational is its suggested recipe. Palette, typography, density, radius, and surfaces remain independent preset choices; the default mathematical artwork uses the accent and its paired foreground tokens.

Try `?preview=course-01&profile=educational&theme=light` in either playground. Course01 is development after immutable registry 0.2.0 and appears under In progress. It is not an installable 0.2.0 block. Its improved Avatar needs matching development framework/core/design packages until a coordinated release.

## Course and lesson data

Import the named Course01 React entry or the default Vue entry. Optional props are course, loading, error, retry, and openLesson. Omitting course uses an explicit fictional sample. Pass a CourseRecord with an empty modules array for an actual course whose curriculum is not ready.

CourseRecord includes id, title, description, subject, level, pace, instructor, outcomes, modules, and resources. Optional coverSrc/coverAlt replace the default decorative artwork. Instructor data includes name, role, bio, optional src, and optional profile href. Avatar supports image failure fallback; the adjacent educator name labels the decorative portrait.

Modules contain id, title, description, and lessons. Each lesson has id, title, summary, positive integer minutes, kind (lesson/practice/checkpoint), status (complete/current/available/locked), optional href, and optional lockReason. IDs are nonempty alphanumeric identifiers with optional hyphens/underscores and must be unique within their collections; lesson IDs are unique throughout the course. At most one lesson can be current. Validation snapshots nested records, validates durations/statuses, and rejects unsafe destinations. Application data must still be authorized before it reaches the client.

Resource records contain id, title, detail, optional href, and optional download. Relative destinations and HTTPS URLs are accepted for lessons, educators, and resources; unsafe URL schemes and protocol-relative URLs are rejected. The original sample practice guide is copied to public/paraxe/course-01/practice-guide.md. It is an editable Markdown asset, not a remote dependency. Replace it and its metadata for your product.

## Progress and navigation

Progress is derived from supplied lesson states: completed count, total, percentage, total duration, and the next lesson/module. Resume prioritizes current, then available, then a completed lesson for review. Fully completed courses and partially completed courses whose remaining content is locked offer review rather than claiming a new lesson is available. All-locked and empty curricula have distinct states; empty curricula do not create a progressbar with a zero maximum.

openLesson receives a copied accessible lesson and may return a promise. When supplied, it takes precedence over lesson href navigation. Opening is locked against duplicates while pending. Rejection leaves progress unchanged and provides an announced retryable error. Course changes and unmounts invalidate stale requests. A direct href is used only when no callback is supplied; a lesson without either destination is unavailable. Locked lessons never launch through the UI or callback guard.

Opening a lesson does not mark it complete. The application owns the learning route/player, completion events, server persistence, enrolment, access checks, and certifications. Client lesson statuses and disabled buttons are not authorization enforcement. Do not award progress merely because navigation succeeded.

## Curriculum behaviour

The existing Accordion and AccordionItem provide native disclosure buttons and linked panels. The resume module opens initially. Search matches module titles and lesson titles/summaries; status filters show all, remaining, or completed lessons. Searching/filtering opens matching modules so results are visible, preserves original lesson numbering, and never alters overall progress. Clear returns to the full curriculum. Module counts/durations describe the original module, while matching-result counts describe the filtered lessons.

The complete page uses Flex and core controls. It can sit inside an application shell without nesting another main landmark. The educator, resources, cover, curriculum, and actions are editable; no extra recipe or prebuilt application shell is required.

Element resets use zero specificity so spacing classes retain their intended margins. The main gutter, rail gaps, hero facts, lesson padding, and section separation use shared density-aware tokens. On small screens lesson statuses occupy a separate row aligned with the lesson text, rather than consuming extra space beside the title.

## Preview and core work

The preview includes a small sample lesson experience with an explicit completion button. It stores progress in tab memory only. About this preview exposes loading, error, empty, completed, and locked states, plus a failed-open simulation. The lesson preview is application/demo code, not another numbered block or a full learning platform.

Core Avatar now renders the declared image/size/shape/status API in React as well as Vue. Shared initials and naming logic support explicit decorative portraits and named statuses. Failed images fall back, source replacements retry correctly, and square avatars use the preset form radius. Circular portraits keep their intended geometry.

Tests cover progress/resume/review edge cases, stable filtering and numbering, invalid identities/destinations, both framework renders, disclosure/search/status interactions, locked and pending guards, failure/retry without completion, explicit sample completion, and Avatar source recovery. Browser visual review remains pending when no connected browser is available.
