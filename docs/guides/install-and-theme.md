# Install and theme an application

Start from an existing Vue 3 or React application. Check framework compatibility with the package you choose; published React declares React/ReactDOM 19. See [release status](../reference/release-status.md).

## Published packages

Vue:

```sh
pnpm add @paraxe/vue@1.3.0 @paraxe/design@1.8.0
pnpm add -D @paraxe/cli@0.3.0
```

React:

```sh
pnpm add @paraxe/react@0.2.0 @paraxe/design@1.8.0
pnpm add -D @paraxe/cli@0.3.0
```

Framework packages bring their core dependency. Install `@paraxe/core@1.4.0` explicitly if you import its contracts/helpers. npm users can substitute `npm install` / `npm install --save-dev` and run the CLI with `npx paraxe`.

## Generate styling

Run from the application's root:

```sh
pnpm exec paraxe init --theme-out src/styles/paraxe-theme.css --preset-out src/styles/paraxe-preset.css --overrides-out src/styles/paraxe-overrides.css
```

Choose a recipe, optionally accept its suggested defaults, then adjust the axes. Published CLI/design support Default, Editorial, Educational, and Clean. Swiss, Brutalist, and Studio currently require development source.

This creates `paraxe.config.json` and project CSS. Regenerate later with `pnpm exec paraxe generate`. An existing override file is preserved.

Import once in `src/main.ts` / `src/main.tsx`:

```ts
import "@paraxe/design/style.css";
import "./styles/paraxe-preset.css";
import "./styles/paraxe-theme.css";
import "./styles/paraxe-overrides.css";
```

The preset imports its recipe. Overrides load last. Do not import another baseline after project rules. For a quick baseline without CLI generation, `@paraxe/design/style.css` alone works.

Set initial mode on the document root, for example `data-theme="light"` and `color-scheme: light`. SSR must render the same initial theme on server and client.

## Components and variants

Import components explicitly from the framework package. Vue's optional `createParaxe` configures variants; it does not globally register every component. React uses `ParaxeProvider` for explicit defaults. Component props override provider/CSS configuration and the fallback.

For SSR, supply the same saved variant map to `createParaxe({ variants })` or `<ParaxeProvider variants={variants}>` on both sides rather than relying on browser CSS during the first render.

## Explore development

In a source checkout:

```sh
pnpm install --frozen-lockfile
pnpm --filter @paraxe/core build
pnpm --filter @paraxe/cli build
pnpm --filter @paraxe/design build
pnpm --filter @paraxe/vue build
pnpm --filter @paraxe/react build
pnpm --filter playground-vue dev
```

Use `pnpm --filter playground-react dev` for React. These playgrounds use workspace packages and canonical block source. Building source does not publish it. Never publish changed contents under an existing npm version. [Publishing](../registry/publishing-commands.md) is a separate maintainer workflow.

