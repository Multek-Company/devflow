# Acme App — Design Conventions

> All color tokens, radii, and base spacing are defined in `resources/css/app.css` via `@theme` and CSS variables. This file covers conventions only.

## Typography

**Font**: Instrument Sans (configured in `@theme` as `--font-sans`)

| Style | Classes | Usage |
|-------|---------|-------|
| Page title | `text-3xl font-bold tracking-tight` | H1 |
| Section title | `text-xl font-semibold` | H2 |
| Card title | `text-base font-medium` | H3, card headers |
| Body | `text-sm` | Default text |
| Caption | `text-xs text-muted-foreground` | Labels, metadata |

## Spacing

| Context | Class |
|---------|-------|
| Page padding | `p-6` |
| Card padding | `p-4` |
| Form fields | `space-y-4` |
| Button groups | `gap-2` |
| Page sections | `space-y-8` |

## Component Usage

Use shadcn/ui components. Key patterns:

- Buttons: `default` for primary actions, `outline` for secondary, `ghost` for tertiary
- Forms: always wrap inputs with `Label`, use `FormField` for validation
- Cards: use `CardHeader` + `CardContent` structure consistently
- Dialogs: `DialogHeader` with `DialogTitle` + `DialogDescription` for accessibility

## Layout

- Sidebar: 256px, uses `sidebar` color tokens
- Content: `max-w-7xl mx-auto px-6`
- Grid: `grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6`
