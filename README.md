# aroragirish.github.io

Personal site for **Girish Aroda** — Associate Architect.
Live at **https://aroragirish.github.io/**

## Structure

```
index.html        Portfolio (single file, no build, no dependencies)
tracker/          Daily Performance Tracker (previous site, still live)
  index.html
.nojekyll         Tells GitHub Pages to serve files as-is
README.md
```

Both pages are self-contained: no npm, no build step, no CDN, no backend,
no analytics. Everything is inline HTML/CSS/JS and uses relative paths, so
either file also works from disk (`file://`) or any static host.

| Page      | URL                                     |
| --------- | --------------------------------------- |
| Portfolio | https://aroragirish.github.io/          |
| Tracker   | https://aroragirish.github.io/tracker/  |

## Deploy

GitHub Pages serves this automatically on push to `main`.

Repo → **Settings** → **Pages** → *Build and deployment*:
**Source:** Deploy from a branch · **Branch:** `main` / `(root)` → Save.

Changes go live roughly 60 seconds after a push.

## Editing the portfolio

Everything lives in `index.html`. The `<style>` block at the top defines the
design tokens — change `--accent` to restyle the whole page.

Sections in order: hero · current role · experience · stack · projects ·
talks & recognition · contact.
