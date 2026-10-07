# Base44 Setup Notes

## Overview
Minimal Node.js test fixture — a single `server.js` serving one HTML page (`/`) and a JSON health check (`/health`). No dependencies, no database, no environment variables.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App binds all interfaces on port 3000 (mapped to host 3000).
- No live-reload dev server: this is a raw `http.createServer` with no watcher. After editing `server.js`, call `reload_preview` so the user sees the change (or `docker compose -f docker-compose.base44.yml restart app`).

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Constraints
- The README asks not to change the app content — E2E tests depend on exact output.
