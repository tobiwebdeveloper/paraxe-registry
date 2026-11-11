# Spinner

A focused loading indicator, implemented in React as well as Vue. Import Spinner from the relevant framework package. React parity and updated motion/size roles ship in React 0.4.0, Vue 1.5.0, and design 1.10.0.

| Prop | Type | Default |
| --- | --- | --- |
| size | sm, md, lg | md |
| label | string | Loading |

```tsx
<Spinner size="sm" label="Loading results" />
```

```vue
<Spinner size="sm" label="Loading results" />
```

A nonempty label provides role status and an accessible name. Use label="" to make the indicator decorative when its parent already provides loading text or a status announcement. Avoid announcing the same pending action multiple times. Spinner does not manage pending state or disable another component.

Size, border, accent, and rotation duration use shared tokens. Rotation stops under prefers-reduced-motion; the ring and status remain available. React accepts className/style; Vue inherits attributes. Try the size examples and pending action in preview=form-composition.
