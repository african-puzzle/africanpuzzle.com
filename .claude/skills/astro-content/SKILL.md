---
name: astro-content
description: Create or edit content collection entries (team members, features, media posts, countries) stored as Markdown/JSON in src/content/. Use when managing CMS content.
argument-hint: [collection] [action] [details?]
---

Manage content in collection `$0`: `$ARGUMENTS`.

## Content Collections

```
src/content/
  config.ts              → collection schemas (Zod)
  team/
    bams-betga.md
    benjamin-mbiandjeu.md
    ...
  features/
    projects.md
    clients.md
    album.md
    appointments.md
  media/
    post-1.md
    ...
  countries/
    countries.json
```

## Schema Pattern (src/content/config.ts)

```ts
import { defineCollection, z } from 'astro:content';

const team = defineCollection({
  type: 'content',
  schema: z.object({
    name: z.string(),
    role: z.object({ fr: z.string(), en: z.string(), pcm: z.string() }),
    linkedin: z.string().url().optional(),
    image: z.string(),
    order: z.number(),
  }),
});
```

## Actions
- **add**: Create new entry with proper frontmatter matching the collection schema
- **edit**: Modify existing entry — read it first, change only what's needed
- **list**: Show all entries in the collection
- **remove**: Delete an entry file

Always validate frontmatter matches the Zod schema in `config.ts`. Include all required fields. Use multilingual objects `{ fr, en, pcm }` for translatable strings.
