---
name: astro-page
description: Create new Astro pages with i18n routing, SEO meta, and proper layout integration. Use when adding a new page to the site.
argument-hint: [page-name] [locale?]
---

Create an Astro page at the correct i18n path for `$ARGUMENTS`.

## i18n Routing Structure

```
src/pages/
  index.astro          → / (redirects to /fr/)
  fr/
    index.astro        → /fr/ (home)
    a-propos.astro     → /fr/a-propos
    contact.astro      → /fr/contact
    medias.astro       → /fr/medias
    confidentialite.astro
  en/
    index.astro        → /en/ (home)
    about.astro        → /en/about
    contact.astro      → /en/contact
    media.astro        → /en/media
    privacy.astro
  pcm/                 → Pidgin English
    index.astro
    ...
```

## Page Template

```astro
---
import Layout from '../../layouts/Layout.astro';
import { getTranslations } from '../../i18n/utils';

const lang = 'fr'; // or 'en' or 'pcm'
const t = getTranslations(lang);
---

<Layout title={t.pageTitle} description={t.pageDesc} lang={lang}>
  <!-- page content using section components -->
</Layout>
```

## Checklist
- [ ] Uses `Layout` wrapper with `title`, `description`, `lang`
- [ ] Loads translations via `getTranslations(lang)`
- [ ] Composes page from section components (not raw HTML)
- [ ] Has equivalent pages in all 3 locales
- [ ] Open Graph and meta tags set via Layout props
