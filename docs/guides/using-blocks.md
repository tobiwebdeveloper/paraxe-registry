# Install and adapt registry blocks

Blocks are editable source compositions. The CLI copies framework entries, shared data/styles, assets, and licenses into your project. It uses Paraxe's own format and installer, with a source-copy approach similar in intent to shadcn.

## Install a released block

After [package/theme setup](install-and-theme.md), run from the application root:

```sh
pnpm exec paraxe list --framework vue
pnpm exec paraxe add faq-01 --framework vue --dry-run
pnpm exec paraxe add faq-01 --framework vue
```

Use `--framework react` for React. Review and install the dependency versions printed by the CLI. It does not install dependencies or run registry scripts.

Registry 0.2.0 contains eighteen blocks in both frameworks: kit-room-collection, navbar-01, product-page-01, hero-01, login-01, footer-01, faq-01, pricing-01, chat-01, cart-01, portal-01, article-01, event-01, studio-01, careers-01, film-01, stay-01, and content-editor-01. Check [release status](../reference/release-status.md) during the coordinated rollout. Registry 0.1.2 remains available for the previous CLI.

## Import copied source

From `src/App.vue` after a project-root install:

```vue
<script setup lang="ts">
import Faq01 from "../blocks/faq-01/vue/Faq01.vue";
const questions = [
  { question: "Can we edit this layout?", answer: "Yes. These files belong to this application." },
];
</script>
<template>
  <Faq01 title="A few useful answers." :items="questions" support-href="" />
</template>
```

From `src/App.tsx`:

```tsx
import { Faq01 } from "../blocks/faq-01/react/Faq01";
export function App() {
  return <Faq01 title="A few useful answers." supportHref="" items={[
    { question: "Can we edit this layout?", answer: "Yes. These files belong to this application." },
  ]} />;
}
```

An empty support destination omits that optional contact action. Supply a route your app actually serves when one exists. The entry imports shared block CSS; application design/preset/theme/override imports are still required.

## Adapt the layout

Replace sample branding, copy, imagery, dates, prices, and destinations. Read the block's own callback contract: authentication, chat, purchasing, enquiries, and registration are separate app integrations.

Keep interface styles token-driven and layout CSS scoped. Reuse existing core controls. Preserve the [typography/control balance](../block-and-recipe-formula.md).

Assets are copied to `public/`. Sample paths usually start at the app root. For subpath hosting, adapt asset data/paths to the host base URL; registry installation does not configure routing or deployment.

[Schema 2](../registry/binary-assets.md), supported by CLI 0.4.0 and registry 0.2.0, copies binary assets exactly. The installer also reads schema 1; CLI 0.3.0 remains pinned to the previous registry 0.1.2.

Existing files are protected. Review dry runs. `--force` replaces files and does not merge edits. Compare a fresh copy and merge deliberately; retain licenses.

Composition examples such as the connected shop and content workspace demonstrate how components and blocks work together. They are not extra installable blocks. Future In progress entries require matching development packages until released.

