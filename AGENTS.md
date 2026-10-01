# AGENTS.md

Minimal Node.js web app (no dependencies, no database, no external credentials).

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts the app on port 3000.
- Uses `node --watch server.js` for live reload on file changes (Node 20 built-in watcher).
- Source is bind-mounted; edits appear without rebuilding the image.

## Verification
- `GET /` returns the page with heading "Base Code E2E" (`data-testid="e2e-marker"`).
- `GET /health` returns `{"status":"ok"}`.

## Notes
- Do not change the page content — E2E tests depend on its exact heading.
- No npm dependencies to install; `package.json` has none.
