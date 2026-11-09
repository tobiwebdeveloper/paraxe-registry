# Vue

Import named components from @paraxe/vue. Value components use v-model and update:modelValue; see their component pages.

For optional auto-imports, use the Paraxe-owned Vite integration:

```ts
import vue from "@vitejs/plugin-vue";
import { ParaxeComponents } from "@paraxe/vue/vite";

export default {
  plugins: [vue(), ParaxeComponents()],
};
```

The wrapper owns the resolver configuration and only recognizes exported Paraxe Vue components. It does not claim RouterLink, RouterView, local components, or arbitrary names.
