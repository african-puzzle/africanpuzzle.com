---
name: design-system
description: Reference for the African Puzzle design system — colors, typography, spacing, component patterns. Loaded by other skills for consistency.
user-invocable: false
---

# African Puzzle Design System

## Brand Colors (Tailwind config)

```js
colors: {
  brand: {
    purple: { 50: '#f3e8ff', 100: '#e9d5ff', 500: '#a855f7', 600: '#8c30f5', 700: '#7c3aed', 900: '#3d2664' },
    blue: { 500: '#3b82f6', 600: '#1F5BFF' },
  }
}
```

**Usage**:
- Primary actions, CTAs, active states → `brand-purple-600`
- Gradients → `from-brand-purple-600 to-brand-blue-600`
- Dark backgrounds → `brand-purple-900` or `slate-900`
- Light section backgrounds → `brand-purple-50` or `slate-50`
- Body text → `slate-700` (light) / `slate-300` (dark)
- Headings → `slate-900` (light) / `white` (dark)

## Typography

- **Font stack**: `'Inter', system-ui, sans-serif` (body), `'Cal Sans', 'Inter', sans-serif` (display headings)
- **Scale**: `text-sm` (14px) → `text-base` (16px) → `text-lg` (18px) → `text-xl` (20px) → `text-2xl` (24px) → `text-4xl` (36px) → `text-5xl` (48px)
- **Weights**: `font-normal` (body), `font-semibold` (subheadings), `font-bold` (headings)
- **Line height**: `leading-relaxed` for body text, `leading-tight` for headings

## Spacing

- Section vertical padding: `py-20 lg:py-28`
- Container: `max-w-7xl mx-auto px-4 sm:px-6 lg:px-8`
- Card padding: `p-6 lg:p-8`
- Stack spacing: `space-y-4` (tight), `space-y-6` (normal), `space-y-8` (loose)
- Grid gaps: `gap-6` (tight), `gap-8` (normal), `gap-12` (loose)

## Component Patterns

### Button
```html
<a class="inline-flex items-center px-8 py-4 bg-brand-purple-600 text-white font-semibold rounded-full shadow-lg hover:bg-brand-purple-700 hover:shadow-xl transition-all duration-300 transform hover:-translate-y-0.5">
```

### Card
```html
<div class="bg-white dark:bg-slate-800 rounded-2xl shadow-lg p-6 hover:shadow-xl transition-all duration-300 hover:-translate-y-1">
```

### Section Heading
```html
<div class="text-center max-w-3xl mx-auto mb-16">
  <span class="text-brand-purple-600 font-semibold text-sm uppercase tracking-wider">Label</span>
  <h2 class="mt-3 text-4xl font-bold text-slate-900 dark:text-white">Heading</h2>
  <p class="mt-4 text-xl text-slate-600 dark:text-slate-300">Subtext</p>
</div>
```

### Badge
```html
<span class="inline-flex items-center px-3 py-1 rounded-full text-sm font-medium bg-brand-purple-50 text-brand-purple-700">
```

## Animations

- **Hover lift**: `hover:-translate-y-1 hover:shadow-xl transition-all duration-300`
- **Fade in**: Use `@keyframes fadeIn` with Intersection Observer for scroll reveals
- **Gradient shift**: `bg-[length:200%_200%] animate-gradient` for animated gradient backgrounds

## Dark Mode

Use Tailwind `dark:` variants. Toggle class-based: `<html class="dark">`.
Key overrides: backgrounds `dark:bg-slate-900`, cards `dark:bg-slate-800`, text `dark:text-white` / `dark:text-slate-300`.

## Icons

Use Astro Icon with the `lucide` icon set. Consistent sizing: `w-5 h-5` (inline), `w-8 h-8` (feature icons), `w-12 h-12` (large decorative).
