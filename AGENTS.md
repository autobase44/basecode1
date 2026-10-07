# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables. Serves a static page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on host port 3000.
- No migrations, no seeds, no secrets required.

## Important
- **Do not modify `server.js`, `package.json`, or `README.md`** — the Base44 E2E tests depend on their exact content.
- This app has no live-reload dev server (`node server.js` is a plain process). After editing source, restart the `web` service (`docker compose -f docker-compose.base44.yml restart web`) or call `reload_preview` so changes are visible.
- Source is bind-mounted into the container, so edits are picked up on restart without rebuilding the image.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`
