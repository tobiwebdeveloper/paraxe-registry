# AvatarGroup

A compact group of replaceable portraits or initials, with bounded visible members and an overflow count. The data API and React parity are **development after registry 0.3.0**. Published Vue has slot composition only; published React does not export this component.

```tsx
import { AvatarGroup } from '@paraxe/react';
<AvatarGroup members={team} max={3} size="sm" label="Hiring team" />
```

```vue
<AvatarGroup :members="team" :max="3" size="sm" label="Hiring team" />
```

Vue imports from `@paraxe/vue`. Each member has a unique nonempty `id`, `name`, and optional Avatar `src`/`status`. IDs are keys, not DOM IDs. `max` defaults to 3 and must be a positive safe integer. `size` defaults to `sm` and accepts Avatar sizes. Internal avatars are decorative; the root image name includes the contextual `label` (default People), every member name, and supplied statuses, including members hidden behind +N. Empty data is hidden from accessibility APIs. Set `decorative` when nearby content already provides every relevant name.

Omit `members` to retain child/slot composition; in that mode you own child semantics. An optional label gives the root a group name. AvatarGroup is a display element, not a menu or people picker. Portrait loading and presence remain app-owned. Overlap, ring, overflow typography and surfaces consume shared tokens. See [Application01](../registry/application-01.md) for a real block setting.
