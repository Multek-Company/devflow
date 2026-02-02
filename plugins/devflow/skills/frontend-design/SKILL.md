---
name: frontend-design
description: This skill should be used when the user asks to "build a UI component", "create a page", "style a component", "improve frontend quality", or any task involving frontend implementation. Builds production-grade, polished interfaces using React, Tailwind CSS, and shadcn/ui — following the project's design system with high attention to detail.
version: 0.3.0
---

# Frontend Design Skill

Build production-grade, polished frontend interfaces. Every output should look like it was crafted by a senior engineer who cares about design — not auto-generated with defaults.

## Where the Design System Lives

The design system is the **project's CSS** — the `@theme` block, `:root` variables, and `.dark` overrides in `app.css` / `globals.css`. That is the single source of truth for colors, radii, and spacing tokens.

Before writing any frontend code:

1. **Read the project's CSS** (`app.css`, `globals.css`, or equivalent) to understand all tokens
2. **Check for a `design-system.md`** (project root, `docs/`, or `.claude/`) for conventions CSS can't express — typography hierarchy, component patterns, layout rules, branding tone etc.
3. **Check existing components** for established patterns

If the project has no Tailwind theme configured, suggest using the `create-tailwind-theme` command to generate one from visual references.

## Stack Conventions

Primary stack: **React + Tailwind CSS + shadcn/ui + TypeScript**. Adapt if the project uses something else.

### Tailwind CSS

- All design tokens come from the `@theme` block and CSS variables — never hardcode colors, spacing, or radii
- Use semantic classes (`bg-primary`, `text-muted-foreground`, `border-destructive`) not arbitrary values
- Respect the project's color format (oklch, hsl, hex — match what exists)
- Extend via `@theme` only when genuinely needed, not for one-off values
- Use responsive prefixes (`sm:`, `md:`, `lg:`) following project breakpoints

### shadcn/ui

- Use shadcn/ui components as the foundation
- Extend through the existing variant API before creating wrappers
- Follow the project's component directory structure
- Use `cn()` for conditional class merging

### React & TypeScript

- Functional components with proper TypeScript interfaces
- Follow existing patterns for state management, data fetching, routing
- `forwardRef` for reusable primitives

## Quality Standards

Follow the design system. Execute it well.

The difference between good and generic isn't breaking rules — it's caring about the details within the rules. When working inside an existing design system:

- **Visual hierarchy**: Every screen needs a clear focal point. Use font weight, size, and color contrast to guide the eye — don't make everything the same weight
- **Spacing**: Be deliberate. Group related elements tightly, separate sections generously. Don't just slap `p-4` on everything — let the content breathe where it should and cluster where it should
- **Composition**: Avoid walls of same-sized cards, monotonous lists, uniform grids. Vary element sizes, use whitespace strategically, create rhythm
- **Typography**: Respect the type scale. Use the project's hierarchy consistently — don't invent new sizes. Make headings, body, and captions clearly distinct
- **Color with purpose**: Use the accent/primary palette to draw attention to what matters. Muted tones for secondary content. Don't distribute color evenly — be intentional
- **Micro-details**: Proper border radii, consistent icon sizing, aligned baselines, hover/focus states that feel polished — these small things compound into quality

### Production Quality

- Responsive at all breakpoints
- Keyboard accessible, proper focus management
- Dark/light mode via the project's theme system
- No console errors, no layout shifts
- Semantic HTML with ARIA attributes

## Creative Mode

**Activates when**: the user explicitly asks for creative, distinctive, or unique design — OR the task is inherently creative (landing pages, marketing pages, hero sections, greenfield UI with no established design system).

When in creative mode, go beyond the design system. Commit to a **bold aesthetic direction**:

### Design Thinking

Before coding, understand the context:
- **Purpose**: What problem does this interface solve? Who uses it?
- **Tone**: Pick a clear direction — brutally minimal, maximalist chaos, retro-futuristic, organic/natural, luxury/refined, playful/toy-like, editorial/magazine, brutalist/raw, art deco/geometric, soft/pastel, industrial/utilitarian. Use these as starting points but design something true to the specific context.
- **Constraints**: Technical requirements (framework, performance, accessibility).
- **Differentiation**: What makes this memorable? What's the one thing someone will remember?

**CRITICAL**: Choose a clear conceptual direction and execute it with precision. Bold maximalism and refined minimalism both work — the key is intentionality, not intensity.

### Frontend Aesthetics

- **Typography**: Choose fonts that are distinctive and elevate the design. Avoid generic defaults (Inter, Roboto, Arial). Pair a characterful display font with a refined body font.
- **Color & Theme**: Commit to a cohesive aesthetic. Dominant colors with sharp accents outperform timid, evenly-distributed palettes.
- **Motion**: Use `tw-animate-css` or Motion library when available. Focus on high-impact moments: one well-orchestrated page load with staggered reveals creates more delight than scattered micro-interactions. Scroll-triggering and hover states that surprise.
- **Spatial Composition**: Unexpected layouts. Asymmetry. Overlap. Diagonal flow. Grid-breaking elements. Generous negative space OR controlled density.
- **Atmosphere & Depth**: Create depth rather than defaulting to flat solid colors. Gradient meshes, noise textures, geometric patterns, layered transparencies, dramatic shadows, grain overlays — whatever serves the vision.

Match implementation complexity to the aesthetic vision. Maximalist designs need elaborate code with extensive animations. Minimalist designs need restraint, precision, and careful attention to spacing and subtle details.

No two creative outputs should look the same. Vary themes, fonts, aesthetics. Never converge on common defaults across generations.

## Quality Checks

Before completing any frontend task:

- All colors reference semantic tokens from the CSS variables
- All spacing uses Tailwind scale values
- Typography matches established hierarchy
- Components follow shadcn/ui patterns
- Dark mode renders correctly
- No hardcoded values that should be tokens
- Accessibility: contrast, semantic HTML, ARIA, keyboard nav

## Available MCP Tools

- **Playwright MCP** — Test UI in a real browser
- **Chrome DevTools MCP** — Debug CSS, console, network
- **Context7 MCP** — Current docs for React, Tailwind, shadcn/ui
- **shadcn MCP** — Browse and install shadcn/ui registry components, check available items
- **Postgres MCP** — Query data when building data-driven UI

## Resources

- **`references/design-system-template.md`** — Template for conventions docs
- **`references/component-checklist.md`** — Pre-implementation checklist
- **`examples/design-system-example.md`** — Sample conventions doc
