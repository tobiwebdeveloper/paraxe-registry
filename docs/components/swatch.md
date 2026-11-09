# Swatch

A small color sample, independently reusable inside a Choice, beside a label, or in product metadata. It owns no selection, heading, layout, inventory, or filter state.

```vue
<Choice value="black" width="auto">
  <Flex as="span" align="center" size="small"><Swatch color="#171717" />Black</Flex>
</Choice>
```

```tsx
<Swatch color="var(--brand-primary)" label="Brand color" size="small" />
```

Import from `@paraxe/vue` or `@paraxe/react`. Props: required `color` (CSS color), optional `label`, `size` (`small`, `medium`, `large`, default medium), and `shape` (`circle` or `square`, default circle). Omit label when a visible color name already accompanies it; this makes the dot decorative. With a label it is an accessible image, never a button by itself. For selection, compose it inside an existing control.

Uses theme border/background tokens and `--swatch-size` for local geometry customization. Blocks own placement and surrounding text.
