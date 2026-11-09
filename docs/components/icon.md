# Icon

Icon is a public React component. Its shared API is defined by `IconProps` from `@paraxe/core`.

## When to use it

Use Icon when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Icon to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import


```tsx
import { Icon } from "@paraxe/react";
```

## Props

| Prop | Type | Default | Required | Description |
| --- | --- | --- | --- | --- |
| `name` | `string` | {name | Yes | Defined by the core contract. |
| `size` | `IconSize` | "inherit" | No | Defined by the core contract. |
| `label` | `string` | {label | No | Defined by the core contract. |



## Usage



### React

```tsx
import { Icon } from "@paraxe/react";

export function Example() {
  return <Icon name={value}>Content</Icon>;
}
```

## Accessibility

Without `label`, Icon sets `aria-hidden`; provide `label` when the icon needs an accessible name.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
