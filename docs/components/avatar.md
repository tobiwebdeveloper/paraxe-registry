# Avatar

Development after registry 0.2.0 brings React into parity with the declared AvatarProps API: src, alt, name, size, shape, and status. Vue also recovers when a failed source is replaced. Shared avatarInitials/avatarLabel helpers produce fallback initials and accessible naming. Use alt="" for a decorative portrait beside a visible name; a named avatar includes its supplied status in the accessible label. Square shape follows the preset form radius; circles preserve their geometry. See [Course01](../registry/course-01.md) for an educator example. These changes require matching development packages until the next release.

Avatar renders a stable-size portrait or initials fallback. Its shared API is AvatarProps from core; the current workspace supports the same declared props in both frameworks. The previously published React implementation supports child text only, so check [release status](../reference/release-status.md) before using the newer props.

## When to use it

Use Avatar when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Avatar to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import


```ts
import { Avatar } from "@paraxe/vue";
```

```tsx
import { Avatar } from "@paraxe/react";
```

## Props

| Prop | Values | Default | Purpose |
| --- | --- | --- | --- |
| src | string | none | Replaceable portrait URL. |
| alt | string | name | Accessible portrait name; an empty string makes the whole avatar decorative. |
| name | string | none | Initials fallback and default accessible name. |
| size | xs, sm, md, lg, xl | md | Shared size classes. |
| shape | circle, square | circle | Circles preserve geometry; square uses the preset form radius. |
| status | online, busy, away, offline | none | App-supplied presence indicator; appended to a named avatar's accessible label. |

Children (React) or the default slot (Vue) replace the initials fallback when no working image is present. A failed image falls back, and changing src retries the image. Neither portraits nor presence are fetched from an account service automatically.



## Usage



### React

```tsx
import { Avatar } from "@paraxe/react";

export function Example() {
  return <Avatar name="Maya Chen" src="/people/maya.jpg" size="lg" />;
}
```

### Vue

```vue
<script setup lang="ts">
import { Avatar } from "@paraxe/vue";
</script>
<template>
  <div>
    <Avatar name="Maya Chen" src="/people/maya.jpg" alt="" size="lg" />
    <span>Maya Chen</span>
  </div>
</template>
```

## Accessibility

Use name or meaningful alt for a standalone portrait. Use alt="" when an adjacent name already labels the same person, as in the Vue example. The wrapper supplies the image semantics; the nested img uses an empty alt to avoid duplicate announcements. Avatar is not interactive; wrap it in a properly named link or button when a profile action is required. Supply status from real application data rather than implying online presence from the image alone.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
