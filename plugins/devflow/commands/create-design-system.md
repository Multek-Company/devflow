---
name: create-design-system
description: Interactive Q&A that builds a comprehensive design-system.md covering stack, branding, typography, icons, layout, component conventions, dark mode, and accessibility.
arguments:
  - name: output-path
    description: Where to save design-system.md (default: project root)
    required: false
---

# Create Design System

You are building a comprehensive design system document through an interactive conversation with the user.

## Process

Walk through the following topics **one group at a time**. For each group, ask the user clear questions using `AskUserQuestion`. Provide sensible defaults so the user can move fast, but let them customize everything.

### 1. Stack

Ask about:
- **Framework**: Next.js, Remix, Vite + React, Astro, etc.
- **CSS approach**: Tailwind CSS, CSS Modules, styled-components, vanilla CSS
- **Component library**: shadcn/ui, Radix, MUI, Chakra, Headless UI, custom
- **State management**: React Context, Zustand, Redux, Jotai, none yet

### 2. Branding

Ask about:
- **Brand name**: Name of the product/project
- **Personality/tone**: e.g. professional & trustworthy, playful & casual, bold & edgy, minimal & refined
- **Existing brand colors**: Any hex/rgb values, or a general direction (e.g. "blues and greens")
- **Existing guidelines**: Link or file to existing brand guidelines, if any
- **Existing logos**: Ask for clear paths regarding brand logos in the project.

### 3. Typography

Ask about:
- **Font preferences**: Specific fonts already chosen, or style preference (geometric sans, humanist, serif, monospace)
- **Type scale needs**: Standard web scale, compact/dense UI, editorial/large headings
- **Font source**: Google Fonts, self-hosted, system fonts

### 4. Icons

Ask about:
- **Icon library**: Lucide, Heroicons, Phosphor, Tabler, FontAwesome, custom SVGs
- **Icon style**: Outline, solid, duotone

### 5. Language & i18n

Ask about:
- **Primary language**: English, or other
- **RTL support**: Needed?
- **i18n setup**: Already configured? Which library (next-intl, react-i18next, none)?

### 6. Layout Patterns

Ask about:
- **Navigation**: Sidebar, top nav, both, bottom tabs (mobile)
- **Content width**: Fixed max-width, full-width, mixed
- **Responsive strategy**: Mobile-first, desktop-first, specific breakpoints of note

### 7. Component Conventions

Ask about:
- **Button styles**: Rounded, pill, square? Primary/secondary/ghost variants needed?
- **Form patterns**: Inline labels, floating labels, stacked? Validation style?
- **Cards**: Bordered, shadow, flat? Consistent or varied?
- **Modals/dialogs**: Centered overlay, slide-over panel, drawer?

### 8. Dark Mode

Ask about:
- **Required?**: Yes/no
- **Default theme**: Light, dark, or system preference
- **Implementation**: CSS variables, class-based toggle, media query only

### 9. Accessibility

Ask about:
- **WCAG level target**: AA (standard), AAA (enhanced), or no specific target
- **Focus indicators**: Default browser, custom styled
- **Motion sensitivity**: Respect `prefers-reduced-motion`?

## Output

After gathering all answers, generate a single **`design-system.md`** file that covers:

1. **Overview** — Project name, stack summary, design philosophy
2. **Colors** — Primary, secondary, accent, destructive, muted palettes with semantic naming. If the user provided brand colors, build the palette around them. If not, propose a cohesive palette matching their stated tone.
3. **Typography** — Font families, type scale (H1–H6, body, caption, overline), weight usage, line heights
4. **Spacing** — Base unit, spacing scale, when to use tight vs generous spacing
5. **Icons** — Library, size conventions, usage guidelines
6. **Layout** — Navigation pattern, content width, grid/column system, responsive breakpoints
7. **Component Patterns** — Buttons, forms, cards, modals, tables, lists — conventions for each
8. **Dark Mode** — Strategy, token mapping approach
9. **Accessibility** — Target level, focus management, motion, contrast requirements
10. **Language & i18n** — Direction, translation approach

Write the file to the path specified by `output-path`, or to the project root as `design-system.md` by default.

## Important

- Ask questions in batches (group related topics) — don't overwhelm with everything at once.
- Provide smart defaults for every question so the user can accept and move on quickly.
- The output should be a practical reference document, not abstract theory. Include concrete class names, token names, and component examples where relevant.
- If the project already has a CSS theme (Tailwind `@theme` block, CSS variables), read it first and incorporate those existing tokens into the design system doc rather than inventing new ones.
- If no theme exists yet, suggest running `create-tailwind-theme` to generate one from visual references.
