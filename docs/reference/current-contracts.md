# Current component contracts

Generated from the development workspace. This is an exact contract snapshot, not a promise that every field is in npm. Check [release status](release-status.md) and the installed package declarations before using an API. Regenerate with `pnpm docs:api`.

Framework components add native attributes and framework events; see [core usage](../guides/core-components.md) and the framework source for those details.

## packages/core/src/contracts/commerce/Price.ts

```ts
/** Amounts are in major currency units (e.g. 48.5 GBP), not minor units. */
export interface PriceProps {
  size?: "inline" | "detail" | "display";
  amount: number;
  currency: string;
  /** Explicit locale avoids server/client formatting differences. */
  locale: string;
  compareAt?: number;
  currentLabel?: string;
  originalLabel?: string;
}
```

## packages/core/src/contracts/commerce/ProductCard.ts

```ts
import type { PriceProps } from "./Price";

export interface ProductCardProps extends PriceProps {
  name: string;
  href: string;
  imageSrc?: string;
  imageAlt: string;
  imageFallbackText?: string;
  category?: string;
  badge?: string;
  availability?: "available" | "unavailable";
  unavailableLabel?: string;
}
```

## packages/core/src/contracts/commerce/ProductGallery.ts

```ts
export interface ProductGalleryImage {
  id: string;
  src?: string;
  alt: string;
  thumbnailSrc?: string;
}
export interface ProductGalleryProps {
  images: readonly ProductGalleryImage[];
  /** Controlled image ID. An absent/removed ID displays the first image. */
  modelValue?: string;
  label?: string;
  imageLabel?: string;
  fallbackText?: string;
}
```

## packages/core/src/contracts/commerce/ProductMedia.ts

```ts
export interface ProductMediaProps {
  as?: "div" | "span";
  src?: string;
  alt: string;
  pending?: boolean;
  fallbackText?: string;
}
```

## packages/core/src/contracts/commerce/QuantityInput.ts

```ts
export interface QuantityBounds {
  min?: number;
  max?: number;
  /** Positive integer increments, anchored at min. */
  step?: number;
}

export interface QuantityInputProps extends QuantityBounds {
  id: string;
  label: string;
  modelValue: number;
  name?: string;
  disabled?: boolean;
  readonly?: boolean;
  hideLabel?: boolean;
  size?: "small" | "medium" | "large";
  decreaseLabel?: string;
  increaseLabel?: string;
}
```

## packages/core/src/contracts/composites/Accordion.ts

```ts
export type AccordionVariant = "divided" | "bordered" | "plain";
export interface AccordionProps {
  multiple?: boolean;
  collapsible?: boolean;
  defaultOpen?: string[];
  variant?: AccordionVariant;
}
```

## packages/core/src/contracts/composites/AccordionItem.ts

```ts
export interface AccordionItemProps {
  id: string;
  disabled?: boolean;
  /** Show the shared plus/minus indicator. */
  indicator?: boolean;
  headingLevel?: "h2" | "h3" | "h4" | "h5" | "h6";
}
```

## packages/core/src/contracts/composites/ButtonGroup.ts

```ts
export type ButtonGroupAlign = "start" | "center" | "end";

export interface ButtonGroupProps {
  align?: ButtonGroupAlign;
  stack?: boolean;
}
```

## packages/core/src/contracts/composites/PageHeader.ts

```ts
export interface PageHeaderProps {
  title: string;
  description?: string;
  bordered?: boolean;
}
```

## packages/core/src/contracts/composites/SectionHeader.ts

```ts
export type SectionHeaderWidth = "default" | "wide";
export type SectionHeaderAlign = "left" | "center";

export interface SectionHeaderProps {
  width?: SectionHeaderWidth;
  align?: SectionHeaderAlign;
}
```

## packages/core/src/contracts/composites/Stat.ts

```ts
export type StatVariant = "default" | "plain";
export type StatTrend = "up" | "down" | "neutral";

export interface StatProps {
  label: string;
  value: string | number;
  trend?: StatTrend;
  change?: string;
  variant?: StatVariant;
}
```

## packages/core/src/contracts/data/Chart.ts

```ts
export interface ChartSeries {
  name: string;
  data: number[];
  /** Any CSS colour. Defaults to the theme's `--chart-color-N` ladder. */
  color?: string;
}

export interface ChartDatum {
  label: string;
  value: number;
  color?: string;
}

export type LineChartVariant = "line" | "smooth" | "area" | "step";

export interface LineChartProps {
  series: ChartSeries[];
  labels?: string[];
  height?: number;
  variant?: LineChartVariant;
  showGrid?: boolean;
  showLegend?: boolean;
  showDots?: boolean;
  format?: (value: number) => string;
  /** Accessible description of the chart. */
  label?: string;
}

export type BarChartVariant = "grouped" | "stacked" | "horizontal" | "stacked-horizontal";

export interface BarChartProps {
  series: ChartSeries[];
  labels?: string[];
  height?: number;
  variant?: BarChartVariant;
  showGrid?: boolean;
  showLegend?: boolean;
  format?: (value: number) => string;
  label?: string;
}

export type DonutChartVariant = "donut" | "pie";

export interface DonutChartProps {
  data: ChartDatum[];
  variant?: DonutChartVariant;
  size?: number;
  /** Ring thickness as a fraction of the radius (donut only). */
  thickness?: number;
  showLegend?: boolean;
  format?: (value: number) => string;
  label?: string;
}

export type SparklineVariant = "line" | "area" | "bars";

export interface SparklineProps {
  data: number[];
  /** Fixed scale bounds, useful when comparing percentages or several trends. */
  min?: number;
  max?: number;
  variant?: SparklineVariant;
  width?: number;
  height?: number;
  color?: string;
  /** Colour by direction (positive/negative) instead of the series colour. */
  trend?: boolean;
  label?: string;
}

export interface ChartLegendItem {
  label: string;
  color: string;
  value?: string;
}
```

## packages/core/src/contracts/data/EmptyState.ts

```ts
export interface EmptyStateProps {
  as?: string;
}

export interface EmptyStateSlots {
  default?: unknown;
  icon?: unknown;
  actions?: unknown;
}
```

## packages/core/src/contracts/data/List.ts

```ts
export type ListValue = string | number;

export type ListModelValue =
  | ListValue
  | ListValue[]
  | null;

export type ListVariant = "default" | "card" | "separated" | "flush";

export type ListSize = "sm" | "md" | "lg";

export interface ListProps {
  selectable?: boolean;
  multiple?: boolean;
  variant?: ListVariant;
  size?: ListSize;
}

export interface ListContext {
  selectable: boolean;
  multiple: boolean;
  isSelected: (value: ListValue) => boolean;
  toggleSelection: (value: ListValue) => void;
}
export interface ListItemProps {
  value: string | number;
  disabled?: boolean;
  title?: string;
  description?: string;
}
```

## packages/core/src/contracts/data/Pagination.ts

```ts
export type PaginationVariant = "default" | "outline" | "filled" | "minimal";

export type PaginationShape = "square" | "round";

export interface PaginationProps {
  label?: string;
  currentPage: number;
  totalItems: number;
  pageSize: number;

  siblingCount?: number;
  compact?: boolean;
  variant?: PaginationVariant;
  shape?: PaginationShape;
}
export interface PaginationEmits {
  (event: "update:currentPage", page: number): void;
}
```

## packages/core/src/contracts/data/Table.ts

```ts
export interface TableColumn<T = unknown> {
  key: string;
  label: string;

  sortable?: boolean;

  width?: string;

  align?: "start" | "center" | "end";

  render?: (value: unknown, row: T) => unknown;
}

export interface TableProps<T = unknown> {
  columns: TableColumn<T>[];
  rows: T[];

  rowKey?: string;

  sortable?: boolean;
  selectable?: boolean;
  multiple?: boolean;

  loading?: boolean;
  empty?: boolean;
  caption?: string;
  emptyText?: string;
  loadingText?: string;
  /** Controlled selection within the supplied rows. Aggregate pages in the app. */
  selectedRows?: T[];
  /** Data key used to name each selection checkbox. */
  rowLabel?: string;
}
```

## packages/core/src/contracts/elements/Avatar.ts

```ts
export type AvatarSize = "xs" | "sm" | "md" | "lg" | "xl";
export type AvatarShape = "circle" | "square";
export type AvatarStatus = "online" | "busy" | "away" | "offline";

export interface AvatarProps {
  src?: string;
  alt?: string;
  name?: string;
  size?: AvatarSize;
  shape?: AvatarShape;
  status?: AvatarStatus;
}
```

## packages/core/src/contracts/elements/AvatarGroup.ts

```ts
import type { AvatarProps, AvatarSize } from "./Avatar";
export interface AvatarGroupMember
  extends Omit<AvatarProps, "size" | "shape" | "alt"> {
  id: string;
  name: string;
}
export interface AvatarGroupProps {
  /** Omit to preserve child/slot composition. */
  members?: readonly AvatarGroupMember[];
  max?: number;
  size?: AvatarSize;
  label?: string;
  decorative?: boolean;
}
```

## packages/core/src/contracts/elements/Badge.ts

```ts
export type BadgeVariant =
  | "default"
  | "success"
  | "warning"
  | "danger"
  | "info"
  | "brand";

export interface BadgeProps {
  variant?: BadgeVariant;
}
```

## packages/core/src/contracts/elements/Button.ts

```ts
export type ButtonVariant =
  | "primary"
  | "secondary"
  | "destructive"
  | "ghost"
  | "text";
// Text actions remain real buttons with the same disabled/focus semantics.

export type ButtonSize =
  | "small"
  | "medium"
  | "large";

export type ButtonWidth =
  | "auto"
  | "full";

export type ButtonIconPosition =
  | "leading"
  | "trailing";

export interface ButtonProps {
  type?: "button" | "submit" | "reset";
  variant?: ButtonVariant;
  size?: ButtonSize;
  width?: ButtonWidth;
  iconPosition?: ButtonIconPosition;
  disabled?: boolean;
  loading?: boolean;
}

export interface ButtonEvents {
  activate: void;
}

export interface ButtonContract {
  props: ButtonProps;
  events: ButtonEvents;
}
```

## packages/core/src/contracts/elements/Card.ts

```ts
export type CardVariant =
  | "default"
  | "outlined"
  | "elevated"
  | "interactive"
  | "selected";

export interface CardProps {
  variant?: CardVariant;
  as?: string;
}
```

## packages/core/src/contracts/elements/Icon.ts

```ts
export type IconSize = "xs" | "sm" | "md" | "lg" | "inherit";
export interface IconProps {
  /** A built-in name. Supply either name or custom paths, never both. */
  name?: string;
  /** Trusted SVG path data, rendered as path attributes rather than injected markup. */
  paths?: readonly string[];
  viewBox?: string;
  size?: IconSize;
  label?: string;
}
```

## packages/core/src/contracts/elements/Spinner.ts

```ts
export type SpinnerSize = "sm" | "md" | "lg";

export interface SpinnerProps {
  size?: SpinnerSize;
  label?: string;
}
```

## packages/core/src/contracts/elements/Swatch.ts

```ts
export interface SwatchProps {
  color: string;
  /** Omit for a decorative swatch beside a visible color name. */
  label?: string;
  size?: "small" | "medium" | "large";
  shape?: "circle" | "square";
}
```

## packages/core/src/contracts/feedback/Alert.ts

```ts
export type AlertVariant =
  | "info"
  | "success"
  | "warning"
  | "danger";

export interface AlertProps {
  variant?: AlertVariant;
  dismissible?: boolean;
}

export interface AlertEmits {
  close: () => void;
}
```

## packages/core/src/contracts/feedback/Progress.ts

```ts
export type ProgressVariant =
  | "default"
  | "success"
  | "warning"
  | "danger";

export interface ProgressProps {
  label?: string;
  value?: number;
  max?: number;
  indeterminate?: boolean;
  variant?: ProgressVariant;
  showValue?: boolean;
}
```

## packages/core/src/contracts/feedback/Skeleton.ts

```ts
export type SkeletonVariant =
  | "text"
  | "heading"
  | "avatar"
  | "circle"
  | "button"
  | "default";

export interface SkeletonProps {
  variant?: SkeletonVariant;
  width?: string;
  height?: string;
}
```

## packages/core/src/contracts/feedback/Toast.ts

```ts
export type ToastVariant =
  | "info"
  | "success"
  | "warning"
  | "danger";

export interface ToastProps {
  modelValue?: boolean;
  title?: string;
  variant?: ToastVariant;
  duration?: number;
  dismissible?: boolean;
}

export interface ToastEmits {
  "update:modelValue": (
    value: boolean,
  ) => void;
  close: () => void;
}
```

## packages/core/src/contracts/forms/Calendar.ts

```ts
/** Date-only values use YYYY-MM-DD. The inline calendar does not book time slots. */
export interface CalendarProps {
  modelValue?: string | null;
  defaultMonth?: string;
  min?: string;
  max?: string;
  availableDates?: readonly string[];
  locale?: string;
  weekStartsOn?: 0 | 1;
  disabled?: boolean;
  label?: string;
  today?: string;
}
```

## packages/core/src/contracts/forms/Checkbox.ts

```ts
export interface CheckboxProps {
  id?: string;
  labelledBy?: string;
  describedBy?: string;
  invalid?: boolean;
  modelValue?: boolean;
  name?: string;
  disabled?: boolean;
  required?: boolean;
}
```

## packages/core/src/contracts/forms/Choice.ts

```ts
export interface ChoiceProps {
  value: string | number;
  disabled?: boolean;
  width?: "auto" | "full";
  size?: "small" | "medium" | "large";
}
```

## packages/core/src/contracts/forms/ChoiceGroup.ts

```ts
export interface ChoiceGroupProps {
  modelValue?:
    | string
    | number
    | Array<string | number>
    | null;
  multiple?: boolean;
  disabled?: boolean;
  label?: string;
}

export type RadioGroupProps = ChoiceGroupProps;
export interface ChoiceGroupContext {
  multiple: boolean;
  disabled: boolean;
  isSelected: (value: string | number) => boolean;
  toggleChoice: (value: string | number) => void;
}
```

## packages/core/src/contracts/forms/Combobox.ts

```ts
export interface ComboboxOption {
  value: string;
  label: string;
  description?: string;
  keywords?: readonly string[];
  disabled?: boolean;
}

export interface ComboboxProps {
  options: readonly ComboboxOption[];
  modelValue?: string | null;
  /** Keeps a remote selection's label available outside the current results. */
  selectedOption?: ComboboxOption;
  query?: string;
  /** Disable local filtering when the application supplies search results. */
  filter?: boolean;
  loading?: boolean;
  error?: string;
  clearable?: boolean;
  id?: string;
  name?: string;
  label?: string;
  describedBy?: string;
  required?: boolean;
  disabled?: boolean;
  invalid?: boolean;
  placeholder?: string;
  emptyMessage?: string;
  loadingMessage?: string;
  requiredMessage?: string;
}
```

## packages/core/src/contracts/forms/DatePicker.ts

```ts

```

## packages/core/src/contracts/forms/Fieldset.ts

```ts
export interface FieldsetProps {
  id?: string;
  legend: string;
  description?: string;
  error?: string;
  disabled?: boolean;
  variant?: "default" | "panel";
}
```

## packages/core/src/contracts/forms/FileUpload.ts

```ts
export type FileUploadVariant = "dropzone" | "compact";

export interface FileUploadProps {
  /** Omit for local state; supply for application-controlled selection. */
  files?: readonly File[];
  id?: string;
  describedBy?: string;
  invalid?: boolean;
  accept?: string;
  multiple?: boolean;
  disabled?: boolean;
  variant?: FileUploadVariant;
  /** Maximum size per file in bytes. */
  maxSize?: number;
  /** Maximum selected files; existing app-owned files are never removed. */
  maxFiles?: number;
  label?: string;
  hint?: string;
}

export interface FileUploadRejection {
  file: File;
  reason: "type" | "size" | "duplicate" | "single" | "count";
  message: string;
}
```

## packages/core/src/contracts/forms/FormField.ts

```ts
export interface FormFieldProps {
  id?: string;
  label?: string;
  description?: string;
  error?: string;
  required?: boolean;
  optional?: boolean;
  disabled?: boolean;
}

export type FieldProps = FormFieldProps;

/** Bind to the actual input; the wrapper never mutates children. */
export interface FormFieldControlProps {
  id: string;
  describedBy?: string;
  invalid: boolean;
  required: boolean;
  disabled: boolean;
}
```

## packages/core/src/contracts/forms/Input.ts

```ts
export interface InputProps {
  variant?: "default" | "plain";
  id?: string;
  name?: string;
  autocomplete?: string;
  type?:
    | "text"
    | "email"
    | "password"
    | "number"
    | "tel"
    | "url"
    | "search"
    | "date"
    | "time"
    | "datetime-local"
    | "month"
    | "week";
  placeholder?: string;
  minlength?: number;
  maxlength?: number;
  pattern?: string;
  /** Native numeric/date constraints; validation remains application-owned. */
  min?: string | number;
  max?: string | number;
  step?: string | number;
  modelValue?: string;
  required?: boolean;
  disabled?: boolean;
  readonly?: boolean;
  error?: boolean;
  success?: boolean;
  describedBy?: string;
  invalid?: boolean;
}
```

## packages/core/src/contracts/forms/InputGroup.ts

```ts
/** Layout for one input and optional adornments. Control state remains on the input. */
export interface InputGroupProps {
  invalid?: boolean;
}
```

## packages/core/src/contracts/forms/Radio.ts

```ts
export interface RadioProps {
  id?: string;
  labelledBy?: string;
  describedBy?: string;
  required?: boolean;
  invalid?: boolean;
  modelValue?: string | number | null;
  value: string | number;
  name: string;
  disabled?: boolean;
}
```

## packages/core/src/contracts/forms/Select.ts

```ts
export interface SelectProps {
  required?: boolean;
  describedBy?: string;
  invalid?: boolean;
  variant?: "default" | "plain";
  id?: string;
  name?: string;
  modelValue?: string;
  disabled?: boolean;
  error?: boolean;
  success?: boolean;
}
```

## packages/core/src/contracts/forms/Slider.ts

```ts
export type SliderSize = "sm" | "md" | "lg";

export interface SliderProps {
  modelValue?: number;
  min?: number;
  max?: number;
  step?: number;
  disabled?: boolean;
  label?: string;
  showValue?: boolean;
  size?: SliderSize;
}
```

## packages/core/src/contracts/forms/Switch.ts

```ts
export interface SwitchProps {
  id?: string;
  name?: string;
  labelledBy?: string;
  describedBy?: string;
  required?: boolean;
  invalid?: boolean;
  modelValue?: boolean;
  disabled?: boolean;
}
```

## packages/core/src/contracts/forms/Textarea.ts

```ts
export interface TextareaProps {
  id?: string;
  name?: string;
  autocomplete?: string;
  modelValue?: string;
  disabled?: boolean;
  readonly?: boolean;
  error?: boolean;
  success?: boolean;
  maxlength?: number;
  minlength?: number;
  invalid?: boolean;
  placeholder?: string;
  rows?: number;
  required?: boolean;
  describedBy?: string;
}
```

## packages/core/src/contracts/media/Image.ts

```ts
export type ImageFit = "cover" | "contain";

export type ImageAspectRatio =
| "auto"
| "square"
| "video"
| "portrait"
| "wide";

export interface ImageProps {
    src?: string;
    pending?: boolean;
    fallbackText?: string;
    loading?: "lazy" | "eager";
    alt: string;
    fit?: ImageFit;
    aspectRatio?: ImageAspectRatio;
}

export interface ImageContract {
    props: ImageProps;
}
```

## packages/core/src/contracts/media/Video.ts

```ts
export type VideoAspectRatio = "video" | "wide" | "square" | "portrait" | "auto";
export type VideoVariant = "default" | "bordered" | "cinematic";

export interface VideoTrack {
  src: string;
  kind?: "subtitles" | "captions" | "descriptions" | "chapters" | "metadata";
  srcLang?: string;
  label?: string;
  default?: boolean;
}

export interface VideoProps {
  src?: string;
  poster?: string;
  title?: string;
  controls?: boolean;
  autoplay?: boolean;
  muted?: boolean;
  loop?: boolean;
  aspectRatio?: VideoAspectRatio;
  variant?: VideoVariant;
  /** Show a custom play overlay until playback starts. */
  overlay?: boolean;
  preload?: "none" | "metadata" | "auto";
  tracks?: readonly VideoTrack[];
  fallbackText?: string;
}
```

## packages/core/src/contracts/navigation/Breadcrumb.ts

```ts
export interface BreadcrumbProps {
  href?: string;
  current?: boolean;
}
```

## packages/core/src/contracts/navigation/Breadcrumbs.ts

```ts
export type BreadcrumbsVariant = "default" | "pills" | "filled";

export type BreadcrumbsSize = "sm" | "md" | "lg";

export interface BreadcrumbsProps {
  /** Any string, or "chevron" for an SVG chevron. */
  separator?: string;
  variant?: BreadcrumbsVariant;
  size?: BreadcrumbsSize;
}
```

## packages/core/src/contracts/navigation/Command.ts

```ts

```

## packages/core/src/contracts/navigation/Dropdown.ts

```ts
export type DropdownPlacement =
  | "bottom-start"
  | "bottom-end"
  | "top-start"
  | "top-end";

export interface DropdownProps {
  /** Omit for local open state. */
  modelValue?: boolean;
  /** Stable prefix for the trigger and menu IDs. */
  id?: string;
  /** Visible text for the default trigger. */
  label?: string;
  placement?: DropdownPlacement;
  disabled?: boolean;
}
```

## packages/core/src/contracts/navigation/DropdownMenu.ts

```ts

```

## packages/core/src/contracts/navigation/Menu.ts

```ts
export type MenuVariant = "default" | "flat" | "outline";

export type MenuSize = "sm" | "md" | "lg";

export interface MenuProps {
  id?: string;
  labelledBy?: string;
  variant?: MenuVariant;
  size?: MenuSize;
  label?: string;
}

export interface MenuItemProps {
  id?: string;
  textValue?: string;
  target?: string;
  rel?: string;
  download?: string | boolean;
  href?: string;
  danger?: boolean;
  disabled?: boolean;
  shortcut?: string;
}
```

## packages/core/src/contracts/navigation/Navbar.ts

```ts
export type NavbarVariant =
  | "default"
  | "floating"
  | "transparent"
  | "solid"
  | "glass"
  | "brand";

export type NavbarSize = "sm" | "md" | "lg";

export interface NavbarProps {
  variant?: NavbarVariant;
  size?: NavbarSize;
}
```

## packages/core/src/contracts/navigation/Sidebar.ts

```ts
export type SidebarVariant =
  | "default"
  | "floating"
  | "inset"
  | "minimal"
  | "bordered"
  | "brand";

export type SidebarItemVariant =
  | "default"
  | "indicator"
  | "pill"
  | "outline"
  | "solid";

export interface SidebarProps {
  collapsed?: boolean;
  label?: string;
  variant?: SidebarVariant;
  itemVariant?: SidebarItemVariant;
}

export interface SidebarGroupProps {
  label?: string;
}

export interface SidebarItemProps {
  active?: boolean;
  disabled?: boolean;
  href?: string;
  expanded?: boolean;
  variant?: SidebarItemVariant;
}
```

## packages/core/src/contracts/navigation/Stepper.ts

```ts
export type StepperVariant = "default" | "dots" | "bars" | "vertical";

export interface StepperProps {
  label?: string;
  /** Zero-based index of the current step. */
  current: number;
  steps: string[];
  variant?: StepperVariant;
}
```

## packages/core/src/contracts/navigation/Tab.ts

```ts
export interface TabProps {
  value: string | number;
  disabled?: boolean;
  id?: string;
  controls?: string;
}
```

## packages/core/src/contracts/navigation/Tabs.ts

```ts
export type TabsVariant =
  | "underline"
  | "pills"
  | "segmented"
  | "enclosed"
  | "vertical";

export type TabsSize = "sm" | "md" | "lg";

export interface TabsProps {
  label?: string;
  modelValue?: string | number | null;
  variant?: TabsVariant;
  size?: TabsSize;
  fullWidth?: boolean;
}

export interface TabsEmits {
  "update:modelValue": [
    value: string | number,
  ];
}
```

## packages/core/src/contracts/overlays/Dialog.ts

```ts
export interface DialogProps {
  modelValue?: boolean;
  closeOnBackdrop?: boolean;
  closeOnEscape?: boolean;
}
export interface DialogEmits {
  "update:modelValue": [value: boolean];
}
```

## packages/core/src/contracts/overlays/Drawer.ts

```ts
export interface DrawerProps {
  modelValue?: boolean;
  side?: "left" | "right";
  closeOnBackdrop?: boolean;
  closeOnEscape?: boolean;
}
```

## packages/core/src/contracts/overlays/Popover.ts

```ts
export type PopoverPlacement =
  | "top"
  | "bottom"
  | "left"
  | "right";

export interface PopoverProps {
  placement?: PopoverPlacement;
}
```

## packages/core/src/contracts/overlays/Sheet.ts

```ts

```

## packages/core/src/contracts/overlays/Tooltip.ts

```ts
export type TooltipPlacement =
  | "top"
  | "bottom"
  | "left"
  | "right";

export interface TooltipProps {
  id?: string;
  disabled?: boolean;
  placement?: TooltipPlacement;
  text: string;
  delay?: number;
}
```

## packages/core/src/contracts/primitives/AppShell.ts

```ts
export type AppShellVariant = "default" | "inset";

export interface AppShellProps {
  variant?: AppShellVariant;
  /** In-flow navigation disclosure on narrow screens; this is not a modal. */
  sidebarOpen?: boolean;
  sidebarId?: string;
  mainId?: string;
  mainLabel?: string;
}
```

## packages/core/src/contracts/primitives/Collapsible.ts

```ts

```

## packages/core/src/contracts/primitives/Container.ts

```ts
export type ContainerSize =
  | "default"
  | "narrow";

export interface ContainerProps {
  size?: ContainerSize;
}
```

## packages/core/src/contracts/primitives/Divider.ts

```ts

```

## packages/core/src/contracts/primitives/Flex.ts

```ts
export interface FlexProps {
  as?: "div" | "span";
  inline?: boolean;
  direction?: "row" | "column";
  wrap?: boolean;
  align?: "stretch" | "start" | "center" | "end" | "baseline";
  justify?: "start" | "center" | "end" | "between" | "around" | "evenly";
  size?: "small" | "medium" | "large";
  fullWidth?: boolean;
}
```

## packages/core/src/contracts/primitives/Grid.ts

```ts
export type GridColumns = 1 | 2 | 3 | 4 | 5 | 6;

export type GridRows = 1 | 2 | 3 | 4 | 5 | 6;

export type GridSize =
  | "small"
  | "medium"
  | "large";

export interface GridProps {
  /** Cross-axis alignment of items within each row. */
  align?: "stretch" | "start" | "center" | "end";
  columns?: GridColumns;
  rows?: GridRows;
  size?: GridSize;
}
```

## packages/core/src/contracts/primitives/ScrollArea.ts

```ts

```

## packages/core/src/contracts/primitives/Section.ts

```ts

```

## packages/core/src/contracts/primitives/Separator.ts

```ts

```

## packages/core/src/contracts/primitives/Stack.ts

```ts
export type StackSize =
  | "small"
  | "medium"
  | "large";

export interface StackProps {
  size?: StackSize;
  fullWidth?: boolean;
}
```

## packages/core/src/contracts/typography/Eyebrow.ts

```ts

```

## packages/core/src/contracts/typography/Heading.ts

```ts
export type HeadingLevel =
  | "h1"
  | "h2"
  | "h3"
  | "h4"
  | "h5"
  | "h6";

export interface HeadingProps {
  level?: HeadingLevel;
}
```

## packages/core/src/contracts/typography/Label.ts

```ts
export interface LabelProps {
  for?: string;
  required?: boolean;
  optional?: boolean;
  disabled?: boolean;
}
```

## packages/core/src/contracts/typography/Text.ts

```ts
export type TextTone =
  | "primary"
  | "secondary"
  | "muted"
  | "accent"
  | "inverse"
  | "brand";

export type TextElement =
  | "p"
  | "span"
  | "div";

export interface TextProps {
  as?: TextElement;
  tone?: TextTone;
}
```

