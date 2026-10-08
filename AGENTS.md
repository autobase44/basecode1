# Base44 dev environment

Minimal Node HTTP server (`server.js`) with zero dependencies, no env vars, and no database.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- Web entry point on host port 3000; healthcheck at `GET /health` → `{"status":"ok"}`.
- The source is bind-mounted, but the app has no live-reload dev server — run `reload_preview` after editing `server.js` for changes to appear.

## Notes
- Do NOT change `server.js` / `package.json` / `README.md` content casually — the Base44 E2E tests depend on their exact content (heading "Base Code E2E", `/health` response).
- No external credentials are required.
