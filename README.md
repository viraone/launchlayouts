# LaunchLayouts

A GitHub Pages site showcasing website templates for customers to pick from.

## Structure

```
index.html              Landing page (template gallery, process, pricing, contact)
assets/site.css         Landing page styles
templates/
  spotlight/            Template 01 — personal brand / performer one-pager
    index.html
    style.css
reference/              Screenshots used as design inspiration (not published content)
```

## Adding a new template

1. Copy `templates/spotlight/` to `templates/<name>/`.
2. Edit the HTML/CSS. Swap `.ph` placeholder blocks for real `<img>` tags.
3. Add a new `<article class="template-card">` in `index.html` pointing at `templates/<name>/index.html`.

## Deploy to GitHub Pages

1. Create a repo on GitHub (e.g. `launchlayouts`).
2. In this folder:
   ```
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/<you>/launchlayouts.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Source: Deploy from a branch → `main` / `/ (root)`**.
4. Site goes live at `https://<you>.github.io/launchlayouts/`.

## Before you publish

- Replace `hello@example.com` in `index.html` with your real email.
- Update pricing to what you actually charge.
- Optionally delete `reference/` — those screenshots are of a real person's site and shouldn't be published.
