---
name: perf-audit
description: Audit the Astro site for performance issues — bundle size, image optimization, unused CSS, render-blocking resources, Core Web Vitals.
allowed-tools: Read, Grep, Glob, Bash
context: fork
agent: Explore
---

Perform a performance audit on this Astro site. Check the following and report findings with fixes.

## Checklist

### Build Output
- Run `npm run build` and check `dist/` sizes
- Flag any page HTML over 100KB
- Flag any JS bundle over 50KB (Astro should produce minimal JS)

### Images
- All images use Astro `<Image>` or `<Picture>` (not raw `<img>`)
- Images have explicit `width` and `height` (prevents CLS)
- Large images use `loading="lazy"` (below the fold)
- Hero images use `loading="eager"` and `fetchpriority="high"`
- Images served as WebP/AVIF via Astro's image service

### CSS
- No unused Tailwind classes bloating the bundle (check purge config)
- No render-blocking external stylesheets
- Fonts preloaded with `<link rel="preload">`

### JavaScript
- Minimal client-side JS — only interactive islands
- No unnecessary `client:load` (prefer `client:visible` or `client:idle`)
- Third-party scripts (analytics) loaded with `async` or in `<script>` with `is:inline`

### HTML
- Proper heading hierarchy (h1 → h2 → h3)
- Meta descriptions on all pages
- Open Graph tags present
- `lang` attribute set correctly per locale

### Output
Report as a markdown table: | Issue | File | Severity | Fix |
