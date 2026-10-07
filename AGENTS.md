# Base44 Dev Environment

## Overview
Minimal Node.js web app (no dependencies, no database, no external services). Single file `server.js` uses only `node:http`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App runs from bind-mounted source via `node --watch server.js` (live reload on file changes).
- Web entry point: port 3000 → `GET /` (HTML page, heading "Base Code E2E")
- Health check: `GET /health` → `{"status":"ok"}`

## No secrets required
No environment variables or external credentials are needed to boot.

## Notes
- Node 20+ required (uses built-in `--watch` for live reload; no nodemon/dev server).
- The README says not to change app content — tests depend on exact page content.
