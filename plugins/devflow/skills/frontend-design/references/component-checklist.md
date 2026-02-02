# Component Implementation Checklist

Use this checklist before and after implementing any UI component.

## Pre-Implementation

- [ ] Read the project's `design-system.md` file
- [ ] Check if a similar component already exists in the codebase
- [ ] Identify which design tokens will be needed
- [ ] Determine component variants and sizes required
- [ ] Review the data shape if component displays dynamic data

## During Implementation

### Styling
- [ ] Using design tokens for all colors (no hardcoded hex/rgb)
- [ ] Using spacing scale for all margins, padding, gaps
- [ ] Using typography scale for font sizes and weights
- [ ] Using defined border radius tokens
- [ ] Using defined shadow tokens
- [ ] Semantic color usage (not decorative color choices)

### Structure
- [ ] Semantic HTML elements used appropriately
- [ ] Component follows established file/folder conventions
- [ ] Props API matches existing component patterns
- [ ] Variants follow the naming conventions in the design system

### Responsive
- [ ] Works at all defined breakpoints
- [ ] Uses the grid/layout system from design system
- [ ] Text scales appropriately
- [ ] Touch targets are at least 44x44px on mobile

### Accessibility
- [ ] Color contrast meets WCAG AA (4.5:1 text, 3:1 large text)
- [ ] Keyboard navigation works (Tab, Enter, Escape)
- [ ] Focus indicators are visible
- [ ] ARIA attributes present where needed
- [ ] Screen reader tested (or semantic HTML verified)
- [ ] No information conveyed by color alone

## Post-Implementation

- [ ] Component renders correctly in light and dark themes (if applicable)
- [ ] No console errors or warnings
- [ ] Performance is acceptable (no layout thrashing, excessive re-renders)
- [ ] Component is documented if it's new and reusable
