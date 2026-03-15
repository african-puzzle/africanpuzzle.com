---
name: responsive-audit
description: Audit components and pages for responsive design issues — broken layouts, overflow, missing breakpoints, touch targets, and mobile UX.
allowed-tools: Read, Grep, Glob
context: fork
agent: Explore
---

Audit responsive design across the site. Check all `.astro` files in `src/`.

## Checks

### Layout Issues
- No fixed widths (`w-[500px]`) without responsive alternatives
- Flex/grid containers have proper wrapping (`flex-wrap`, responsive grid cols)
- Images use `max-w-full` or responsive width classes
- No horizontal overflow on mobile (look for wide tables, code blocks, fixed containers)

### Breakpoint Coverage
- Every layout component uses at least `md:` breakpoint
- Grid columns reduce on mobile: `grid-cols-1 md:grid-cols-2 lg:grid-cols-3`
- Font sizes scale: `text-2xl md:text-4xl`
- Padding/margins reduce on mobile: `p-4 md:p-8 lg:p-12`

### Navigation
- Mobile menu exists (hamburger) for `< md:` screens
- Nav links have adequate touch targets (min 44x44px → `p-3` minimum)
- Language selector is accessible on mobile

### Typography
- No text smaller than 16px on mobile (avoid `text-xs` for body content)
- Line lengths capped (`max-w-prose` or `max-w-2xl` for text blocks)
- Headings don't overflow on small screens

### Interactive Elements
- Buttons have minimum touch target size (`px-6 py-3` minimum)
- Form inputs are full-width on mobile
- Hover effects have tap equivalents (`active:` states)

### Output
Report as: | Component | Issue | Breakpoint | Fix |
