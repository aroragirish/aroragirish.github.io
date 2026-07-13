# Daily Performance Tracker

A private, offline-first tracker for a single day. Measure the day, reflect on it, export a report an AI can analyse.

Everything lives in `index.html`. No build step, no npm, no CDN, no backend, no accounts, no analytics. All data stays in your browser's `localStorage` until you export it.

## Deploy to GitHub Pages

1. Create a repository and push these files to the root:
   ```
   index.html
   .nojekyll
   README.md
   ```
2. Repo → **Settings** → **Pages**.
3. Under *Build and deployment*, set **Source: Deploy from a branch**, **Branch: `main` / `(root)`**, then Save.
4. Wait ~60 seconds. The app is live at `https://<your-username>.github.io/<repo-name>/`.

No workflow file, no build, no `base` path to configure — the page uses only relative assets, so it works from any subpath. The same file also works on Vercel, Netlify, Cloudflare Pages, or opened directly from disk (`file://`).

## What's inside

- **Dashboard** — one composite ring where each arc's *thickness is its weight in the score* (Health 25, Productivity 25, Learning 20, Mental wellness 15, Discipline 15), plus live stat tiles.
- **Habits** — 10 defaults with goals and progress bars; add, edit, delete, and pick which pillar each one feeds. Quick-add chips and ± steppers.
- **Tasks** — checklist with unlimited custom items.
- **Learning** — book, pages, tutorial, lesson, key learnings, free notes.
- **Reflection** — the five journal questions, three gratitudes, eight honest questions, tomorrow's plan.
- **Anxiety** — multiple episodes per day: time, mood, intensity, reason, trigger, thoughts, symptoms, how you calmed down, duration, whether it's still with you, what would help next time.
- **Mood** — five faces plus energy / stress / confidence / focus / motivation (stress is scored in reverse).
- **Export** — Markdown (preferred), PDF (via the browser's print dialog — that's how it stays dependency-free), JSON. Plus **Copy AI prompt**, **Copy report**, and **Copy prompt + report** for a one-paste hand-off to Claude, ChatGPT or Gemini.

## Day rollover

If the stored day isn't today and its report was never exported, the app stops and asks: **Download report**, **Discard**, or **Continue anyway**. Choosing *Continue anyway* keeps a banner at the top of every screen until you download or discard it. Nothing is ever deleted silently.

Only one day is stored at a time — by design. Your history lives in the reports you export.

## Keyboard

| Key | Goes to |
| --- | --- |
| `R` | Reading |
| `W` | Water |
| `J` | Journal |
| `E` | Export |

## Data model

```json
{
  "date": "2026-07-13",
  "reportExported": false,
  "dailyData": {
    "habits": [], "tasks": [], "learning": {}, "journal": {},
    "reflection": {}, "anxiety": [], "mood": {}, "score": 84
  }
}
```

Saved to `localStorage` under `dpt.today.v1` (and `dpt.pending.v1` for an un-exported previous day). Autosaves on every keystroke — there is no Save button.
