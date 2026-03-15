---
name: astro-component
description: Create or edit Astro components (.astro files) following project conventions — layouts, islands, props, slots, scoped styles with Tailwind.
argument-hint: [component-name] [description]
---

Create an Astro component named `$0` with purpose: `$ARGUMENTS`.

## Rules

1. **File location**: `src/components/` (nest in subdirs by domain: `ui/`, `sections/`, `layout/`)
2. **Frontmatter**: TypeScript in the `---` fence. Define `Props` interface. Destructure from `Astro.props`.
3. **Styling**: Use Tailwind utility classes. Only use `<style>` for animations or complex selectors not possible in Tailwind.
4. **Slots**: Use named slots for composable layouts. Default slot for main content.
5. **Islands**: Only add `client:*` directives when interactivity is required. Prefer `client:visible` over `client:load`.
6. **Accessibility**: Semantic HTML, ARIA labels where needed, focus states on interactive elements.
7. **Responsive**: Mobile-first. Use Tailwind breakpoints `sm:`, `md:`, `lg:`.
8. **Images**: Use Astro `<Image>` component with explicit `width`/`height` and `alt`.

## Template

```astro
---
interface Props {
  // typed props here
}
const { /* destructured props */ } = Astro.props;
---

<section class="...">
  <slot />
</section>
```

Keep components focused — one responsibility. Extract sub-components when a file exceeds ~80 lines.
