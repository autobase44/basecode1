# Base Code E2E

Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables. Used as a fixture for Base44 Base Code E2E tests — do not change the app's behavior or content; the tests depend on it.

## Running

- `docker compose -f docker-compose.base44.yml up -d` — starts the app on port 3000 from bind-mounted source.
- Source is bind-mounted at `/app`; the container runs `node server.js` directly (no live reload — call `reload_preview` after edits).
- `GET /` returns the fixture page (heading "Base Code E2E"); `GET /health` returns `{"status":"ok"}`.

## Verification

- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with `<h1>Base Code E2E</h1>`
