# FileUpload

A focused local file selector with dropzone/compact surfaces, picker/drop validation, selected-file rows, removal, and rejection feedback. It does not transfer files. The audited Vue implementation, React parity, controlled files, and preset variants are **development after registry 0.3.0**. Published Vue 1.5.0 has the earlier uncontrolled implementation; React 0.4.0 does not export FileUpload. Use matching workspace core/design/framework/CLI packages for this version.

```tsx
const [files, setFiles] = useState<File[]>([]);
<FileUpload files={files} onFilesChange={setFiles} multiple
  accept=".pdf,.txt,image/*" maxSize={5 * 1024 * 1024}
  label="Choose attachments" hint="Documents and images, up to 5 MB each." />
```

```vue
<script setup lang="ts">
import { ref } from 'vue';
import { FileUpload } from '@paraxe/vue';
const files = ref<File[]>([]);
</script>
<template>
  <FileUpload v-model:files="files" multiple accept=".pdf,.txt,image/*"
    :max-size="5 * 1024 * 1024" label="Choose attachments"
    hint="Documents and images, up to 5 MB each." />
</template>
```

React imports FileUpload from @paraxe/react. Vue preserves its existing update:files event; React uses onFilesChange. Omit files for local uncontrolled state. Supply a readonly array for controlled state, and update it from the callback/event. Emitted arrays are new arrays containing the original File objects. Do not switch between controlled and uncontrolled modes during one mount.

## Selection rules

- multiple defaults to false. A valid single-file choice replaces the old file; an entirely rejected attempt keeps it. Extra valid files in one single-mode drop are rejected. Multiple mode appends accepted files.
- Repeated metadata identities (name, size, MIME type, lastModified) are rejected within a multiple selection. This is not content hashing. A single replacement can reselect the same file. The native picker is cleared after each attempt so another selection can fire normally.
- accept supports case-insensitive extensions, MIME types, and MIME wildcards. Picker and dropped files use the same checks. Empty browser MIME metadata can match an extension; a MIME-only rule cannot infer the type from a filename. Invalid accept syntax or negative/noninteger maxSize values throw a configuration error.
- maxSize is a per-file byte limit; undefined has no limit and zero accepts only zero-byte files. Display sizes use 1,024-byte increments.
- A rejected attempt displays filename/reason feedback and emits rejected in Vue or onRejected in React. Entries have file, reason (type/size/duplicate/single), and message. The next nonempty attempt replaces those notices. Rejections never enter selected files.
- disabled blocks selection, drops, and removal. A containing disabled fieldset also blocks interactions. Removing a selected row restores focus to the native picker. Controlled external replacements change the visible list; use an application-owned key/remount when resetting all local notices as well.

Changing accept/maxSize/multiple does not silently delete existing app-owned files. The app should reconcile existing selections when changing policy. Native form reset does not reset the component's list; handle it through controlled state or remounting.

## Labels, styling, and submission

id targets the actual picker and its native label. hint creates linked help; describedBy adds external description IDs; invalid adds an app-owned error state. Rejections have an alert region and updates have a polite status. Compact and dropzone variants consume form radius/height/borders, card surfaces, typography, spacing, and focus roles. Set fileUpload in createParaxe/ParaxeProvider or the development CLI variant map; an explicit variant prop wins. Long filenames wrap while the remove action retains its own space.

The picker deliberately has no name and is cleared after reading. The displayed selection is **not submitted by native FormData(form)** and this component does not supply native required validation. Validate the selected array in the application and append its File objects when submitting:

```ts
const body = new FormData();
for (const file of files) body.append('attachments', file, file.name);
await applicationService.submit(body);
```

The browser exposes selected File objects through its [file-input API](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/input/file). Local name/type/size checks provide feedback; the application server must validate its actual uploads. Transfer progress, cancellation, retries, storage, and permissions belong to that integration. This component invents no upload progress or completion.

Try `?preview=file-upload&profile=clean&theme=light` in either playground. It is an In progress **core-component preview**, not a numbered registry block. It covers multiple attachments, single replacement, compact/disabled states, external reset, and explicit sample selection. Shared logic, both framework renders/provider defaults, and Vue client selection/removal/rejection transitions are tested. Browser visual/native picker review remains pending when the review connection is unavailable.
