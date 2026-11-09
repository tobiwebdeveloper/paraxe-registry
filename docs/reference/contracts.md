# Contract source

Generated from the public `@paraxe/core` barrel. Run `pnpm docs:generate` after changing contracts.

## Accordion

```ts
export interface AccordionProps {
    multiple?: boolean;
    collapsible?: boolean;
    defaultOpen?: string[];
}

```

## AccordionItem

```ts
export interface AccordionItemProps {
  id: string;
  disabled?: boolean;
}
```

## ButtonGroup

```ts
export type ButtonGroupAlign = "start" | "center" | "end";

export interface ButtonGroupProps {
  align?: ButtonGroupAlign;
  stack?: boolean;
}
```

## SectionHeader

```ts
export type SectionHeaderWidth = "default" | "wide";
export type SectionHeaderAlign = "left" | "center";

export interface SectionHeaderProps {
  width?: SectionHeaderWidth;
  align?: SectionHeaderAlign;
}
```

## EmptyState

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

## List

```ts
export type ListValue = string | number;

export type ListModelValue =
  | ListValue
  | ListValue[]
  | null;

export interface ListProps {
  selectable?: boolean;
  multiple?: boolean;
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
}
```

## Pagination

```ts
export interface PaginationProps {
  currentPage: number;
  totalItems: number;
  pageSize: number;

  siblingCount?: number;
  compact?: boolean;
}
export interface PaginationEmits {
  (event: "update:currentPage", page: number): void;
}
```

## Table

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
}
```

## Badge

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

## Button

```ts
export type ButtonVariant =
  | "primary"
  | "secondary"
  | "destructive"
  | "ghost";

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

## Card

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

## Icon

```ts
export type IconSize = "xs" | "sm" | "md" | "lg" | "inherit";

export interface IconProps {
  name: string;
  size?: IconSize;
  label?: string;
}
```

## Alert

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

## Progress

```ts
export type ProgressVariant =
  | "default"
  | "success"
  | "warning"
  | "danger";

export interface ProgressProps {
  value?: number;
  max?: number;
  indeterminate?: boolean;
  variant?: ProgressVariant;
  showValue?: boolean;
}
```

## Skeleton

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

## Toast

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

## Input

```ts
export interface InputProps {
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
  modelValue?: string;
  required?: boolean;
  disabled?: boolean;
  readonly?: boolean;
  error?: boolean;
  success?: boolean;
}
```

## Radio

```ts
export interface RadioProps {
  modelValue?: string | number | null;
  value: string | number;
  name: string;
  disabled?: boolean;
}
```

## Choice

```ts
export interface ChoiceProps {
  value: string | number;
  disabled?: boolean;
}
```

## ChoiceGroup

```ts
export interface ChoiceGroupProps {
  modelValue?:
    | string
    | number
    | Array<string | number>
    | null;
  multiple?: boolean;
  disabled?: boolean;
}

export type RadioGroupProps = ChoiceGroupProps;
export interface ChoiceGroupContext {
  multiple: boolean;
  disabled: boolean;
  isSelected: (value: string | number) => boolean;
  toggleChoice: (value: string | number) => void;
}
```

## Select

```ts
export interface SelectProps {
  id?: string;
  name?: string;
  modelValue?: string;
  disabled?: boolean;
  error?: boolean;
  success?: boolean;
}
```

## Switch

```ts
export interface SwitchProps {
  modelValue?: boolean;
  disabled?: boolean;
}
```

## Textarea

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
}
```

## FormField

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
```

## Checkbox

```ts

export interface CheckboxProps {
  modelValue?: boolean;
  name?: string;
  disabled?: boolean;
  required?: boolean;
}


```

## Image

```ts
export type ImageFit = "cover" | "contain";

export type ImageAspectRatio =
| "auto"
| "square"
| "video"
| "portrait"
| "wide";

export interface ImageProps {
    src: string;
    alt: string;
    fit?: ImageFit;
    aspectRatio?: ImageAspectRatio;
}

export interface ImageContract {
    props: ImageProps;
}
```

## Breadcrumb

```ts
export interface BreadcrumbProps {
  href?: string;
  current?: boolean;
}
```

## Breadcrumbs

```ts
export interface BreadcrumbsProps {
  separator?: string;
}
```

## Sidebar

```ts
export interface SidebarProps {
  collapsed?: boolean;
}

export interface SidebarGroupProps {
  label?: string;
}

export interface SidebarItemProps {
  active?: boolean;
  disabled?: boolean;
  href?: string;
  expanded?: boolean;
}
```

## Tab

```ts
export interface TabProps {
  value: string | number;
  disabled?: boolean;
}
```

## Tabs

```ts
export interface TabsProps {
  modelValue?: string | number | null;
}

export interface TabsEmits {
  "update:modelValue": [
    value: string | number,
  ];
}
```

## Dialog

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

## Drawer

```ts
export interface DrawerProps {
  modelValue?: boolean;
  side?: "left" | "right";
  closeOnBackdrop?: boolean;
  closeOnEscape?: boolean;
}
```

## Popover

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

## Tooltip

```ts
export type TooltipPlacement =
  | "top"
  | "bottom"
  | "left"
  | "right";

export interface TooltipProps {
  placement?: TooltipPlacement;
  text: string;
  delay?: number;
}
```

## Container

```ts
export type ContainerSize =
  | "default"
  | "narrow";

export interface ContainerProps {
  size?: ContainerSize;
}
```

## Grid

```ts
export type GridColumns = 1 | 2 | 3 | 4 | 5 | 6;

export type GridRows = 1 | 2 | 3 | 4 | 5 | 6;

export type GridSize =
  | "small"
  | "medium"
  | "large";

export interface GridProps {
  columns?: GridColumns;
  rows?: GridRows;
  size?: GridSize;
}
```

## Stack

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

## Heading

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

## Label

```ts
export interface LabelProps {
  for?: string;
  required?: boolean;
  optional?: boolean;
  disabled?: boolean;
}
```

## Text

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
