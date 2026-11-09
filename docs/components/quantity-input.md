# QuantityInput

QuantityInput combines a labelled native number input and independent decrement/increment buttons. It is controlled by the app and uses whole, safe-integer quantities, including optional pack increments.

```vue
<QuantityInput id="shirt-quantity" v-model="quantity" name="quantity"
  label="Quantity" :min="1" :max="8" />
```

```tsx
<QuantityInput id="shirt-pack" modelValue={quantity} onModelValueChange={setQuantity}
  name="quantity" label="Pack quantity" min={2} max={9} step={2} />
```

Import from `@paraxe/vue` or `@paraxe/react`; `QuantityInputProps` and `QuantityBounds` are exported from `@paraxe/core`.

| Prop | Type | Default |
| --- | --- | --- |
| id | string, required | Unique input ID, associated with the label/buttons |
| label | string, required | Visible input label |
| modelValue | number, required | Controlled integer quantity |
| name | string | Omitted; set for native form submission |
| min | non-negative safe integer | 1 |
| max | safe integer, at least min | Number.MAX_SAFE_INTEGER |
| step | positive safe integer | 1 |
| disabled | boolean | false |
| readonly | boolean | false |
| hideLabel | boolean | false; visually hides the label but retains its name |
| size | small, medium, large | medium |
| decreaseLabel | string | Decrease quantity |
| increaseLabel | string | Increase quantity |

Vue emits `update:modelValue(number)`; React calls `onModelValueChange(number)`. Buttons commit immediately. Typed edits remain a local draft until blur or Enter; Enter commits without submitting the form. Escape discards the draft. Native number-input arrow-key changes are drafts until committed too. Empty, fractional, negative, exponent, non-finite, and unsafe-number drafts restore the current value; they are never emitted. Valid out-of-range drafts clamp to bounds and off-step drafts round to the nearest allowed quantity (ties round upward).

Steps are anchored at `min`. With `min=2`, `max=9`, `step=3`, valid values are 2, 5, and 8; the effective input maximum is 8. Bounds and step must be safe integers; invalid configuration or a non-integer/non-finite model throws `RangeError`. `min=0` supports zero/removal flows, but removing a cart line remains the app's decision. Use `min=0,max=0` for a zero-only control; both buttons are disabled.

For safety, out-of-range/off-step controlled values render normalized but do not emit on mount or inventory updates. Keep app state consistent when stock changes by using the exported `normalizeQuantity(value, bounds)` helper. `getQuantityBounds(bounds)` exposes the reachable maximum, and `parseQuantity(draft, bounds)` returns a valid value or null for an invalid draft. The component resets its draft when the controlled value, bounds, or disabled/read-only state changes. If the app rejects an emitted update, the control returns to its existing controlled value.

Disabled controls are excluded from native form submission. Read-only controls retain their value for submission and disable both buttons. All action buttons have `type="button"` and names; localize the label and button names (include the product name where several quantity inputs appear together). Medium uses the shared 44px minimum; small uses 36px. Typography and button/input padding use theme/density roles, and `--quantity-input-width` controls the numeric field width.

The component does not enforce server inventory, debounce cart requests, calculate totals, or announce cart mutations. Submit only committed values from app state and validate inventory on the server. Browser interaction, form submission, native arrow-key behavior, and light/dark/narrow-screen visual review remain pending.
