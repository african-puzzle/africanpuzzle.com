---
name: i18n
description: Add or update translations for French, English, and Pidgin. Use when adding new text strings, translating content, or fixing translation issues.
argument-hint: [action] [key?] [text?]
---

Manage translations: `$ARGUMENTS`.

## Translation File Structure

```
src/i18n/
  translations/
    fr.json      → French (default locale)
    en.json      → English
    pcm.json     → Pidgin English
  utils.ts       → getTranslations(), getLocaleFromUrl(), etc.
```

## JSON Structure (flat, dot-notation keys)

```json
{
  "nav.home": "Accueil",
  "nav.about": "À propos",
  "nav.contact": "Contact",
  "nav.download": "Télécharger",
  "nav.media": "Médias",
  "hero.title": "L'application pour s'organiser...",
  "hero.subtitle": "...",
  "features.projects.title": "Programmes",
  "features.projects.desc": "..."
}
```

## Rules
1. **Always update all 3 locale files** when adding a new key
2. Keys are dot-separated: `section.subsection.label`
3. French is the source of truth — translate FROM French
4. Pidgin translations should be natural Pidgin, not literal translations
5. Keep strings short for UI — move long text to content collections instead
6. Use `{placeholder}` for interpolated values: `"greeting": "Bonjour {name}"`

## Helper Usage in Components

```astro
---
import { getTranslations } from '../i18n/utils';
const t = getTranslations(lang);
---
<h1>{t['hero.title']}</h1>
```

## Actions
- **add [key] [fr] [en] [pcm]**: Add a new translation key to all files
- **update [key] [locale] [text]**: Update a specific key in one locale
- **audit**: Check for missing keys across locales
- **sync**: Ensure all locales have the same keys (fill missing with French fallback)
