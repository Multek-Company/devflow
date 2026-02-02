# [Project Name] — Design Conventions

> Colors, radii, and spacing tokens live in the project's CSS (`app.css` / `globals.css`). This file documents conventions that CSS cannot express.

## Typography Hierarchy

| Style | Tailwind Classes | Usage |
|-------|-----------------|-------|
| Page title | `text-3xl font-bold` | H1, page headers |
| Section title | `text-xl font-semibold` | H2, section headers |
| Card title | `text-base font-medium` | H3, card headers |
| Body | `text-sm` | Default body text |
| Caption | `text-xs text-muted-foreground` | Labels, hints |

## Spacing Conventions

| Context | Class |
|---------|-------|
| Page padding | `p-6` |
| Card padding | `p-4` |
| Stack gap | `gap-4` |
| Inline gap | `gap-2` |
| Section gap | `gap-8` |

## Component Patterns (shadcn/ui)

### Button
```tsx
<Button variant="default | secondary | outline | ghost | destructive" size="sm | default | lg">
```

### Input
```tsx
<div className="space-y-2">
  <Label htmlFor="name">Name</Label>
  <Input id="name" />
</div>
```

### Card
```tsx
<Card>
  <CardHeader>
    <CardTitle>Title</CardTitle>
    <CardDescription>Description</CardDescription>
  </CardHeader>
  <CardContent>...</CardContent>
</Card>
```

## Layout

- Max content width: `max-w-7xl mx-auto`
- Responsive: single column mobile, multi-column at `md:`+
- Sidebar (if applicable): fixed width, `flex` layout

## Accessibility

- WCAG AA contrast (4.5:1 text, 3:1 large text)
- Keyboard accessible interactive elements
- Semantic HTML (`<button>`, `<nav>`, `<main>`)
- ARIA labels on icon-only buttons
- Visible focus indicators
