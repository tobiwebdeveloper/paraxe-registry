# Application01

A brief-led recruiting application: company and role masthead, numbered role outcomes, hiring-team context, process notes, and a three-section application dossier. The received and closed states retain the role context. Suggested recipe: **Swiss**; palette, type, density, radius, surface and component variants remain independent.

**Development after registry 0.3.0.** It is visible under In progress and in both recipe studios. The published registry does not yet include this block. Use matching development core, design and framework packages; current npm releases do not contain the newer AvatarGroup, FileUpload and Dropdown contracts used here.

## Preview

[Vue](https://tobiwebdeveloper.github.io/paraxe-registry/preview/vue/?preview=application-01&profile=swiss&theme=light) / [React](https://tobiwebdeveloper.github.io/paraxe-registry/preview/react/?preview=application-01&profile=swiss&theme=light). Hosting may lag source while GitHub Pages is unavailable. Local Vue: `http://127.0.0.1:5175/?preview=application-01&profile=swiss&theme=light`.

The preview uses a fictional role and an explicitly local receipt. It sends no application or files. Example details fill text fields; choose your own local PDF to exercise file validation.

## Own the content and service

Copy the renderer, `shared/application.ts`, and `shared/application.css` together. Create one controller per mounted application or server request. Replace every sample role, location option, focus note, team member and process step. Optional role, careers and privacy destinations must be real relative or HTTPS links. Omitted destinations are hidden.

```ts
import { createApplicationController } from './blocks/application-01/shared/application';
const controller = createApplicationController(role, {
  submit: async ({ requestId, roleId, values, files }) => {
    const body = new FormData();
    body.set('requestId', requestId);
    body.set('roleId', roleId);
    body.set('values', JSON.stringify(values));
    files.resume.forEach(file => body.append('resume', file));
    files.supporting.forEach(file => body.append('supporting', file));
    const response = await fetch('/api/applications', { method: 'POST', body });
    if (!response.ok) throw new Error('Application failed');
    return response.json();
  },
});
```

Render `<Application01 controller={controller} />` in React or `<Application01 :controller="controller" />` in Vue. Supply optional `title` and `description` to change the introduction. The service must return `{ id, roleId, receivedAt, nextStep? }`, with a matching role and valid timestamp containing a timezone. A button click alone never produces a receipt. `ApplicationFieldError` supplies field-level server feedback; `ApplicationClosedError` closes the role while retaining the draft. Validate authorization, file content, size, eligibility and persistence on your server. File extensions and MIME metadata in the browser are convenience checks.

## Draft and interaction contract

- Local validation covers name, email, an enabled location, optional HTTPS portfolio, statement bounds, one PDF CV, supporting-file limits, and the final review checkbox.
- Pending submission guards edits and duplicate sends. An unchanged retry reuses its request key. The server owns idempotency and must return the original receipt for a repeated successful request.
- Failures retain values and original File objects. FileUpload is a selector; the service adapter owns transfer.
- Section links are native anchors; completeness is derived from current values. Validation focuses the first invalid control; receipt/closed transitions focus the status heading.
- Clear draft requires confirmation. `reset()` clears locally; `replace(role)` starts another role and discards its old local draft. Late responses after replacement or `cancelPending()` are ignored. Cancellation does not abort a network request or undo a server submission.
- The Options download generates a real plain-text public role brief. It never includes candidate details.
- There is no automatic persistence. Reloading loses the draft. Handle navigation protection and retention policy in the owning app; do not casually persist application files or personal details in browser storage.

## Layout and styling

The left role brief and right form are independent Flex regions, stacked on narrow screens. Fields wrap intrinsically and display headings accept larger recipes. The form keeps one coherent surface rather than placing every field in a card. Grouping, borders, typography, focus and spacing consume semantic tokens; `--application01-gap` and `--application01-brief-width` are local layout hooks. Use a surrounding page shell to supply navigation and the single main landmark.
