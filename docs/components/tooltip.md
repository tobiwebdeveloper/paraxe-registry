# Tooltip

A short, text-only hint attached to one real trigger. The linked description, Escape dismissal and shared hover/focus behaviour are **development after registry 0.3.0**. Published packages retain the earlier implementation.

```tsx
import { Button, Tooltip } from '@paraxe/react';
<Tooltip text="Keep your current draft.">
  <Button variant="secondary" onActivate={saveDraft}>Save draft</Button>
</Tooltip>
```

```vue
<Tooltip text="Keep your current draft.">
  <Button variant="secondary" @activate="saveDraft">Save draft</Button>
</Tooltip>
```

Vue imports Button/Tooltip from `@paraxe/vue`. Both APIs accept `text`, `placement` (top, bottom, left, right; default top), `delay` (300 ms hover default), optional `id`, and `disabled`. Delay must be finite and nonnegative. Empty text disables the hint. Automatic IDs are instance-specific; explicit IDs must be unique.

## Trigger and interaction

Supply one element, typically a native button/link or Paraxe Button. The component clones its trigger to merge aria-describedby with existing description IDs. Custom trigger components must forward that attribute to their actual focusable element. Fragment/text/multiple-node triggers are unsupported. No wrapper tabstop is added and the trigger's own events are preserved. Native disabled controls cannot receive keyboard focus; keep essential reasons for disabling visible outside the tooltip.

Keyboard focus shows the hint immediately. Pointer hover uses delay. Escape dismisses without moving focus and suppresses reopening during the same engagement. Blur dismisses; moving between trigger and popup has a short grace period so the text stays hoverable. Timers and listeners are removed on disable/unmount. The popup is role tooltip and the trigger references its ID. This follows the interaction guidance in the [WAI tooltip pattern](https://www.w3.org/WAI/ARIA/apg/patterns/tooltip/), which WAI marks as work in progress.

The hint is supplemental. Keep required help, errors and action labels visible. Tooltip has no interactive content; use a nonmodal dialog/popover for links or inputs. It does not take focus or announce through a live region.

## Styling and limits

Surface, border, typography, radius, motion, focus context and spacing follow shared tokens. `--tooltip-surface`, `--tooltip-text`, `--tooltip-border` and `--tooltip-radius` are overridable roles; radius follows the card treatment by default and text uses caption typography. Width is bounded to the viewport, but placement remains **inline CSS**, without collision flipping or a portal. An overflow-clipping ancestor can clip the popup; choose another placement or visible help there. Native browser/screen-reader review remains separate from helper and renderer tests.

[Core preview](https://tobiwebdeveloper.github.io/paraxe-registry/preview/vue/?preview=icons&profile=clean&theme=light).
