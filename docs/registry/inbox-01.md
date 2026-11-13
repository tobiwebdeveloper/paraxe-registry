# Inbox01

A conversation desk: searchable mailbox rail, readable message history and reply composer, plus a separate contact/context rail. Suggested recipe **Clean**; palette, typography, density, radius, surfaces and icon family remain independent. On narrower screens context moves below the conversation, then the mailbox becomes a bounded list above it.

**Development after registry 0.3.0.** [Vue](https://tobiwebdeveloper.github.io/paraxe-registry/preview/vue/?preview=inbox-01&profile=clean&theme=light) / [React](https://tobiwebdeveloper.github.io/paraxe-registry/preview/react/?preview=inbox-01&profile=clean&theme=light). The preview's messages/archive actions are local simulations, not delivered emails. It is a new layout, not a connected application example renamed as a block.

## Data and service

Copy the renderer, shared/inbox.ts and shared/inbox.css together. Create one controller per app view or server request with your InboxRecord. Supply brand/title/locale/agentName and conversations with unique IDs, explicit unread/archive states, contact information, context fields and messages. Each message has an author, direction, nonblank body and explicit ISO instant with timezone. Replace all fictional contacts/copy. Dates display in UTC with explicit locale. Unread state is supplied by your application; merely selecting a row does not claim server-side read persistence.

```ts
const controller = createInboxController(data, {
  reply: async ({ requestId, threadId, body }) => {
    const response = await fetch('/api/conversations/reply', {
      method: 'POST', headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ requestId, threadId, body }),
    });
    if (!response.ok) throw new Error('Reply failed');
    return response.json(); // { threadId, message }
  },
  archive: async ({ threadId, archived }) => {
    // Persist through your authenticated application service.
    return saveArchiveState(threadId, archived); // { threadId, archived }
  },
});
```

Render `<Inbox01 controller={controller} />` in React or `<Inbox01 :controller="controller" />` in Vue. Services are optional; unavailable actions are disabled rather than inventing success. Reply creation returns a canonical outgoing message for the requested conversation. Archive responses must match the requested conversation and new state. Reply content is text, not HTML.

## Behaviour and boundaries

The copied controller owns the local immutable snapshot, inbox/unread/archive filters, full-history search, active selection and drafts per conversation. Reply validation allows 1 to 4,000 trimmed characters. Pending work blocks repeated sends and editing that conversation's draft. Navigating to another conversation preserves drafts and correlates late responses to their original thread. Failures retain the draft; unchanged retries reuse the request key. The service must implement idempotency and authoritative delivery/persistence. A matching response is required before adding an outgoing message or changing archive state.

replace(data) validates and resets the view, invalidating old responses. It does not abort requests or undo server actions. Archive/restore keeps local drafts; changing mailbox/search reconciles the active selection. Successful replies mark that local conversation read. Real-time updates, unread persistence, pagination, attachments, permissions, delivery guarantees and backend integrations remain app-owned and are not implied by this first layout.

Native buttons expose current selection and control the detail region. Core Tabs identify the active mailbox panel. Reply controls use FormField; status and failure feedback stay visible. Messages and contact fields wrap; no fixed-height message viewport truncates large recipe typography. The shared Icon component follows whichever registered family the app selects. --inbox01-list-width and --inbox01-context-width are local layout hooks.

Automated tests cover search/empty states, separate drafts, pending guards, stable retries, wrong/stale responses, archive recovery, linked IDs and client editing. Native browser and optical review are separate pending checks when the browser connection is unavailable.
