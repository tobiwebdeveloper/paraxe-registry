# Navbar

Navbar is a shared native header primitive in Vue and React with brand, content, and actions regions. It owns no routes, cart data, link labels, or edition text; those belong in registry blocks.

```vue
<Navbar variant="solid">
  <template #brand><a href="/">Home</a></template>
  <nav aria-label="Main navigation">...</nav>
  <template #actions>...</template>
</Navbar>
```

```tsx
<Navbar variant="solid" brand={<a href="/">Home</a>} actions={actions}>
  <nav aria-label="Main navigation">...</nav>
</Navbar>
```

Import from `@paraxe/vue` or `@paraxe/react`. `NavbarProps` comes from core. Variant accepts default/floating/transparent/solid/glass/brand; size accepts sm/md/lg. Defaults are default and md. React accepts className/style/native header attributes; Vue supports fallthrough attributes. Use native links and a labelled nav region in content; consumers supply current-link state and meaningful names.

See the [reference blocks](../registry/reference-blocks-01.md) for Navbar01 composition.
