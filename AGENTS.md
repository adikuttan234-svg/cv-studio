# AGENTS.md

## Project overview
CV Studio is a **static, browser-only CV builder**. The entire app lives in a single `index.html` file (with inline CSS and JS). There is no backend, no build step, no package manager, and no server-side code. CV data is stored in browser `localStorage`.

## Running in the sandbox
The app is served as static files via nginx in `docker-compose.base44.yml` on host port 3000. No build or compilation is needed.

```
docker compose -f docker-compose.base44.yml up -d
```

## Architecture notes
- `index.html` — the entire application (HTML + CSS + JS inline, ~200KB).
- `404.html`, `robots.txt`, `sitemap.xml`, `site.webmanifest` — static supporting files.
- `netlify.toml` / `vercel.json` — deployment configs for external hosts (not used in the sandbox).
- No dependencies, no migrations, no seeds, no environment variables required.

## Editing
Edits to `index.html` (or any static file) are served immediately by nginx — no reload step needed. Use `reload_preview` only if the browser cache needs busting.
