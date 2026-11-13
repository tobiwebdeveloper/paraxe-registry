# Icon

A local SVG symbol with identical Vue and React drawing data, inherited colour, token-sized geometry and optional accessible naming. **Development after registry 0.3.0.** Published core/framework packages still have the earlier text-name placeholder. The built-in set needs no font, network icon lookup, vendor runtime or SVG HTML injection. Optional vendor adapters are described below.

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

## Lucide and Tabler adapters (development)

The provider integration and optional adapters are development after registry 0.3.0, requiring matching newer framework/core packages. Current npm releases do not contain these exports. The recipe studio now reads preset.iconLibrary for Lucide/Tabler and retains that field in exported/shared presets. Icon family is a runtime choice, not a colour/CSS axis.

### React

Install only the vendor packages you use: `pnpm add lucide-react` and/or `pnpm add @tabler/icons-react`.

```tsx
import { ParaxeProvider, Icon } from '@paraxe/react';
import { lucideIcons } from '@paraxe/react/icons/lucide';
import { tablerIcons } from '@paraxe/react/icons/tabler';
import config from './paraxe.config.json';
<ParaxeProvider icons={{
  library: config.preset.iconLibrary,
  libraries: { lucide: lucideIcons, tabler: tablerIcons },
}}>
  <Icon name="search" size="sm" />
</ParaxeProvider>
```

### Vue

Install `pnpm add @lucide/vue` and/or `pnpm add @tabler/icons-vue`. Lucide's current Vue package is [@lucide/vue](https://lucide.dev/guide/version-1); the older lucide-vue-next name belongs to its earlier release line.

```ts
import { createParaxe } from '@paraxe/vue';
import { lucideIcons } from '@paraxe/vue/icons/lucide';
import { tablerIcons } from '@paraxe/vue/icons/tabler';
import config from './paraxe.config.json';
app.use(createParaxe({ icons: {
  library: config.preset.iconLibrary,
  libraries: { lucide: lucideIcons, tabler: tablerIcons },
} }));
```

Use a reactive configuration object to change the selected family in a running Vue app. React follows provider prop changes; a nested provider that changes only variants inherits icon configuration. The studio demonstrates switching without rewriting the blocks. Remove imports and registrations for any unused family in a product.

Both optional maps cover the common Paraxe semantic names. The base package entry does not import vendor code; adapters have optional peer dependencies. Importing a common map includes its curated set, not just one symbol. For the smallest application-specific set, register explicit vendor components instead:

```tsx
import { Search, Folder } from 'lucide-react';
const icons = { library: 'lucide', libraries: {
  lucide: { ...lucideIcons, search: Search, 'project-folder': Folder },
} };
```

Omit the spread and map only the needed symbols when that is preferable. Vue accepts its corresponding SVG component mappings. These are trusted application components that must forward SVG size/class/style and accessibility attributes. No runtime icon network lookup or injected SVG markup is introduced. Vendor licensing remains with the imported packages; do not copy their drawings without their licence notices.

`<Icon library="tabler" name="search" />` overrides the selected family, but that family must be registered. `library="builtin"` explicitly selects the original local path set. Custom paths bypass vendor selection. Inherited colour, size classes, stroke token, decorative hiding and named role img stay consistent; data-icon-library records the renderer actually used. An unregistered family or missing symbol throws a useful error. Set provider fallback to builtin explicitly to permit missing common symbols to use the local set; a missing family still throws.

Heroicons/Phosphor preset values are preserved and may use explicit application mappings; bundled adapters for them are not supplied yet. In the studio, such a saved preset shows a notice and uses the built-in set until Lucide/Tabler is selected. It is not silently relabelled as a supported vendor.
