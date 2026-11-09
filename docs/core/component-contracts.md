# Component contracts

This is the public contract for Paraxe components. It applies to Vue and React unless a framework-specific difference is documented on the component page.

## Naming

- Use semantic singular names such as Button, Dialog, Field, and RadioGroup.
- Prefer Field and RadioGroup for new code. FormField and ChoiceGroup remain compatibility names.
- Use compound components when a parent owns child state, such as Tabs with Tab and Accordion with AccordionItem.

## State and events

- Vue value components use v-model and emit update:modelValue.
- React value components accept modelValue and call onModelValueChange.
- Boolean open/closed components follow the same model-value convention.
- Components must not keep a second unsynchronised source of truth when controlled by the caller.

## Variants and extension

- variant describes meaning or visual treatment; size describes geometry.
- Vue components accept normal fallthrough attributes when their root element can receive them.
- Stable React primitives expose className and style; new components must follow the same rule.
- Native identity attributes such as id, name, and autocomplete belong on form controls.

## Accessibility

- Use the native element that already owns the required semantics whenever possible.
- Every interactive control needs an accessible name, visible focus, disabled behavior, and keyboard behavior.
- Composite widgets own their ARIA relationships and focus rules.
- Field labels must point at the control id.
- Do not use color as the only signal for error, selection, or status.

## Compatibility

- Add a new canonical name as an alias before removing an old name.
- Keep aliases behaviorally identical and document removals before a breaking release.
