# Accordion

Shared disclosure group for Vue and React. Use `AccordionItem` children with IDs unique within each group. DOM IDs are scoped to the group instance, so separate groups may reuse item IDs.

## Props

| Prop | Values | Default |
| --- | --- | --- |
| variant | divided, bordered, plain | divided or preset default |
| multiple | boolean | false |
| collapsible | boolean | true |
| defaultOpen | string[] | [] |

`defaultOpen` is initial state, not controlled state. Single-open groups use the first initial ID. Explicit variants take priority over project defaults from `createParaxe`/`ParaxeProvider` and generated preset CSS.

## Vue

```vue
<Accordion :default-open="['delivery']">
  <AccordionItem id="delivery">
    <template #trigger>How does delivery work?</template>
    Delivery information belongs here.
  </AccordionItem>
</Accordion>
```

Import both components from `@paraxe/vue`.

## React

```tsx
<Accordion defaultOpen={["delivery"]}>
  <AccordionItem id="delivery" trigger="How does delivery work?">
    Delivery information belongs here.
  </AccordionItem>
</Accordion>
```

Import both components from `@paraxe/react`.

## Presentation and accessibility

The core owns borders, row spacing, typography, focus states, disabled treatment, and plus/minus indicators. Bordered groups follow the preset form radius and accordion surface. Project overrides can replace the `--accordion-*` roles. Tab reaches each enabled trigger; native buttons support Enter/Space activation. Trigger headings default to h3; set each item's `headingLevel` to match its surrounding document. Linked trigger/panel IDs and `aria-expanded` describe disclosure state. Closed panels use `hidden`.

See [AccordionItem](accordion-item.md) and [block quality](../registry/block-quality.md).
