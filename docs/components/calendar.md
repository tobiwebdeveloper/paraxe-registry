# Calendar

An inline, controlled single-date calendar in Vue and React. It renders a month grid, locale weekday headings, bounded month controls, optional availability, and one date in the keyboard tab order. Calendar ships in core 1.6.0, design 1.10.0, Vue 1.5.0, and React 0.4.0. See [release status](../reference/release-status.md).

```tsx
import { Calendar } from '@paraxe/react';
const [date, setDate] = useState('2026-11-16');
<Calendar modelValue={date} onModelValueChange={setDate}
  min="2026-11-01" max="2026-12-31"
  availableDates={['2026-11-16', '2026-11-17']}
  locale="en-GB" label="Choose an appointment date" />
```

```vue
<script setup lang="ts">
import { ref } from 'vue';
import { Calendar } from '@paraxe/vue';
const date = ref('2026-11-16');
</script>
<template>
  <Calendar v-model="date" min="2026-11-01" max="2026-12-31"
    :available-dates="['2026-11-16', '2026-11-17']"
    locale="en-GB" label="Choose an appointment date" />
</template>
```

## Date and availability ownership

Values, min/max bounds, availableDates, and optional today use real Gregorian YYYY-MM-DD dates, not timestamps. defaultMonth uses YYYY-MM. Selection is controlled through modelValue and the framework event. The component keeps its displayed month and keyboard focus locally; browsing does not change the selected value. A changed controlled value brings that date into view. Changing defaultMonth after mount does not reset the calendar.

Omit availableDates to allow every date within bounds; an empty array allows none. Disabled/unavailable dates remain readable and keyboard-focusable for context but cannot emit selection. Global disabled disables all controls and removes the date tab stop. Selection supplied by an application remains visible even if it is outside availability; the application owns reconciling changed availability with its value. Bounds clamp navigation, not the caller's stored value.

Pass modelValue or defaultMonth explicitly for deterministic server/client rendering. Otherwise initial focus uses the first in-bound available date, then the current UTC date. today is deliberately explicit: applications choose the visitor's relevant date and timezone rather than silently mixing server and browser clocks. locale defaults to en-GB; weekStartsOn accepts 1 (Monday, default) or 0 (Sunday).

## Keyboard and styling

Tab enters the date grid once. Arrow keys move by day/week, Home/End to the beginning/end of the configured week, Page Up/Down by month, and Shift plus Page Up/Down by year. Enter/Space uses the native button action. Month navigation keeps focus on its navigation button. Full weekday names accompany shortened column headings; month changes have a polite live label. The inline interaction follows the relevant grid keyboard guidance in the [WAI-ARIA date-picker example](https://www.w3.org/WAI/ARIA/apg/patterns/dialog-modal/examples/datepicker-dialog/); this component does not create a dialog.

Calendar consumes shared form height/radius/border, button size, typography, brand/foreground, disabled, focus, spacing, and surface tokens. Palette, recipe, density, and radius stay independently editable. It does not fetch availability, reserve a time, select a range, open a popover, or persist an appointment. [Booking01](../registry/booking-01.md) supplies one concrete composition above it.

Shared date arithmetic, renderer semantics in both frameworks, and client keyboard/selection transitions are tested. Browser optical review and assistive-technology review remain pending when a review connection is unavailable.
