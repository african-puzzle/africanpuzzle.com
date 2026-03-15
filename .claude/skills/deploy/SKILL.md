---
name: deploy
description: Build and deploy the Astro site to GitHub Pages. Checks build, verifies output, and manages GitHub Actions workflow.
disable-model-invocation: true
---

Deploy the site to GitHub Pages.

## Steps

1. **Pre-flight checks**:
   - Run `npm run build` and verify no errors
   - Check `dist/` output size and page count
   - Verify all locale pages exist in output

2. **GitHub Actions workflow** (`.github/workflows/deploy.yml`):
   ```yaml
   name: Deploy to GitHub Pages
   on:
     push:
       branches: [main]
     workflow_dispatch:
   permissions:
     contents: read
     pages: write
     id-token: write
   jobs:
     build:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v4
         - uses: actions/setup-node@v4
           with:
             node-version: 20
             cache: npm
         - run: npm ci
         - run: npm run build
         - uses: actions/upload-pages-artifact@v3
           with:
             path: dist/
     deploy:
       needs: build
       runs-on: ubuntu-latest
       environment:
         name: github-pages
         url: ${{ steps.deployment.outputs.page_url }}
       steps:
         - id: deployment
           uses: actions/deploy-pages@v4
   ```

3. **Custom domain**: Ensure `public/CNAME` contains `africanpuzzle.com`

4. **Verify**: After push, check deployment status with `gh run list --workflow=deploy.yml`

## Astro Config for GitHub Pages

```ts
// astro.config.mjs
export default defineConfig({
  site: 'https://africanpuzzle.com',
  output: 'static',
});
```
