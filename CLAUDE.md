# CLAUDE.md

## Project
Static site hosted on **GitHub Pages** (deploy from `main`, root `/`).
URL: `https://jwitkin.github.io/public/`

## Tech decisions
- Single-file HTML apps, no build step, no frameworks
- **Supabase** for cross-device sync via REST API (`fetch()`), no JS SDK — avoids CDN dependency
  - Project: `https://sfsuqaolbjrnoorosibs.supabase.co`
  - Table `packing_lists`: generic key-value store (text `id`, JSONB `state` + `data`), reusable for future lists
  - Anon key embedded in HTML (public by design, RLS handles access)
  - Polls every 3s for remote changes
- localStorage as offline fallback
- List identity via URL hash (`#henry-coe-2026`); new hash = new list
