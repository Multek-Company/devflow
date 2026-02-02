---
name: create-tailwind-theme
description: Analyze screenshots of an interface to extract colors, typography, spacing, and generate Tailwind CSS theme variables (@theme block, :root, .dark) ready to use in the project.
arguments:
  - name: output-path
    description: Where to save the generated CSS (default: prints to chat)
    required: false
---

# Create Design System

You are extracting a Tailwind CSS theme from visual references (screenshots, mockups, design files).

## Process

1. **Ask for screenshots**: Request the user to share screenshots or images of the interface they want to capture. Read every image provided.

2. **Extract from the visuals**:
   - **Color palette**: Identify all colors — backgrounds, text, borders, primary actions, destructive states, accents, brand colors. Extract precise values.
   - **Typography**: Font families visible, size hierarchy, weight variations
   - **Spacing patterns**: Padding, gaps, margins used across the interface
   - **Border radius**: Sharp, rounded, pill — identify the base radius
   - **Shadows**: Elevation levels used
   - **Dark/light**: If both themes are shown, extract both

3. **Generate Tailwind CSS output**: Produce a complete CSS file with:
   - `@theme` block mapping semantic tokens to CSS variables
   - `:root` with light mode values in oklch format
   - `.dark` with dark mode values in oklch format
   - Font family imports if identifiable
   - The `--radius` base value

   Follow the shadcn/ui variable naming convention:
   `--primary`, `--primary-foreground`, `--secondary`, `--muted`, `--destructive`, `--accent`, `--background`, `--foreground`, `--card`, `--border`, `--input`, `--ring`, etc.

4. **Present the CSS** to the user so they can review and paste into their `app.css` or `globals.css`.

5. **Generate a `design-system.md`** with the conventions CSS cannot express: typography hierarchy (which classes for H1, H2, body, caption), component usage patterns, spacing conventions, layout rules. Never duplicate color values — those live in the CSS.

## Output

Two artifacts:
1. **Tailwind CSS** — `@theme` block + `:root` + `.dark` ready to paste into the project's stylesheet
2. **`design-system.md`** — conventions doc covering typography, spacing, component patterns, layout

## Important

- Extract real values from the screenshots. Never use generic defaults.
- Use oklch color format for all values.
- Match shadcn/ui token naming exactly so components work out of the box.
- If a color role isn't visible in the screenshots, ask the user rather than guessing.
