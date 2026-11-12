# Icon

A local SVG symbol with identical Vue and React drawing data, inherited colour, token-sized geometry and optional accessible naming. **Development after registry 0.3.0.** Published core/framework packages still have the earlier text-name placeholder. No font, network icon lookup, third-party icon runtime or SVG HTML injection is required.

```tsx
import { Icon } from '@paraxe/react';
<Icon name="search" size="sm" />
<Icon name="check" label="Completed" />
<Icon paths={['M12 3 21 12 12 21 3 12z']} viewBox="0 0 24 24" />
```

```vue
<script setup lang="ts">
import { Icon } from '@paraxe/vue';
</script>
<template><Icon name="arrow-up-right" size="sm" /></template>
```

## Drawing and names

Supply exactly one of `name` or `paths`. Built-ins include directional arrows/chevrons, check, close, plus, minus, search, menu, mail, calendar, clock, user, download, upload, info, warning, external-link, copy, edit, trash, play, pause, lock, bag, heart, sun, moon and globe. Import `ICON_NAMES` from core for the complete list. The symbols are original small path drawings, not a compatibility layer for Iconify names. Existing playgrounds may still demonstrate independent icon libraries.

Unknown names, empty paths, ambiguous definitions and invalid view boxes throw a configuration error instead of silently showing text. Custom `paths` are SVG path-data strings. Path data from another library can be adapted explicitly; this path-only API does not support every SVG fill, mask or illustration. Use trusted application assets for complex artwork. Never inject untrusted SVG markup. `viewBox` defaults to `0 0 24 24` and needs four finite values with positive width and height.

## Size and accessibility

`size` accepts `inherit` (default), xs, sm, md and lg. Inherited geometry is one em; explicit sizes use `--icon-size-*`. Colour uses currentColor and stroke weight uses `--icon-stroke-width`. Vue inherits class/style attributes; React accepts className/style.

Icons without a nonblank `label` are decorative and hidden from accessibility APIs. A labelled symbol is role img with its accessible name. SVG never adds a tabstop. In a button with visible text, keep the icon decorative. An icon-only button needs an accessible name on the **button**, not merely on its SVG. Icon is not a button or an animation player.

[Core preview](https://tobiwebdeveloper.github.io/paraxe-registry/preview/vue/?preview=icons&profile=clean&theme=light). These changes also replace Footer01's text arrows with real geometry.
