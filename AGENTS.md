# AGENTS.md

## Project Overview
Minimal Node.js web app (no dependencies, no database, no external services).
Single file: `server.js` — serves an HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App listens on port 3000, bound to all interfaces.
- No live-reload dev server; `node server.js` runs directly. Use `reload_preview` after edits.
- No environment variables or secrets required.

## Verification
- `GET /` → HTML page with heading "Base Code E2E"
- `GET /health` → `{"status":"ok"}`
