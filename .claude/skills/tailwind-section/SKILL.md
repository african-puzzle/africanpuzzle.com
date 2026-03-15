---
name: tailwind-section
description: Design polished, responsive page sections using Tailwind CSS with modern web design patterns. Use when building hero sections, feature grids, CTAs, testimonials, or any visual section.
argument-hint: [section-type] [description]
---

Build a `$0` section: `$ARGUMENTS`.

## Design System Tokens

Reference the project's design system (see `/design-system` skill) for colors, typography, and spacing. Key values:

- **Primary**: purple-600 (`#8c30f5` equivalent in Tailwind)
- **Dark**: purple-900/slate-900
- **Accent**: blue-600
- **Radius**: `rounded-2xl` for cards, `rounded-full` for buttons/badges
- **Shadows**: `shadow-lg` for elevated cards, `shadow-sm` for subtle depth
- **Max width**: `max-w-7xl mx-auto` for content containers
- **Section padding**: `py-20 px-4 sm:px-6 lg:px-8`

## Section Patterns

| Type | Layout | Key Classes |
|------|--------|-------------|
| Hero | Centered text + CTA | `min-h-[80vh] flex items-center justify-center text-center` |
| Features | Grid 1→2→3 cols | `grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8` |
| Benefits | Icon + text rows | `flex items-start gap-4` per item |
| Team | Card grid | `grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6` |
| CTA | Centered banner | `bg-gradient-to-r from-purple-600 to-blue-600 text-white rounded-2xl p-12 text-center` |
| Stats | Horizontal counters | `flex flex-wrap justify-center gap-12` |

## Rules
1. Mobile-first — start with single column, expand with breakpoints
2. Use `transition-all duration-300` for hover effects
3. Add `hover:shadow-xl hover:-translate-y-1` to interactive cards
4. Use `bg-gradient-to-br` for colorful backgrounds
5. Generous whitespace — `space-y-6` between text blocks
6. Typography hierarchy: `text-4xl font-bold` → `text-xl text-gray-600` → `text-base`
7. Dark mode: add `dark:` variants for all colors
8. Never hardcode pixel widths — use Tailwind's spacing scale
