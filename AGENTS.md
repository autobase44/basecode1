# Base Code E2E — Base44 Setup Notes

## Overview
Minimal Node.js HTTP server (no dependencies, no database, no external services).

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000, serves HTML at `/` and JSON at `/health`.
- Source is bind-mounted; no live-reload watcher (project has no dev script or nodemon). Use `reload_preview` after edits.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Constraints
- README warns: do not change `server.js` or `package.json` — E2E tests depend on their exact content.
