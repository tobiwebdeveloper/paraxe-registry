# Avatar

This React-only export renders a `span.avatar` around its children. It has no public props contract.

## When to use it

Use Avatar when its semantic structure and contract match the interface pattern. Use it as a focused building block; compose it with ordinary application markup where no companion component is required.

## When not to use it

Do not use Avatar to simulate a different semantic control or invent undocumented states. Choose native HTML when no Paraxe behaviour or styling contract is needed.

## Import


```tsx
import { Avatar } from "@paraxe/react";
```

## Props

No public props are declared for this component.



## Usage



### React

```tsx
import { Avatar } from "@paraxe/react";

export function Example() {
  return <Avatar>Content</Avatar>;
}
```

## Accessibility

Use meaningful child content and preserve the semantics of the rendered element. See Foundations > Accessibility for shared responsibilities.

## Related

- [Component index](../reference/component-index.md)
- [Core contracts](../core/contracts.md)
