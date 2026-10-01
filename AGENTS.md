# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (no dependencies, no database, no external services).
Single file: `server.js` — serves an HTML page at `/` and JSON health at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App listens on port 3000 (mapped to host 3000).
- Uses `node --watch server.js` for live reload on file changes — no rebuild needed after edits.

## Verification
- `curl localhost:3000/health` → `{"status":"ok"}`
- `curl localhost:3000/` → HTML page with heading "Base Code E2E"
- Container healthcheck hits `/health` every 10s.

## Notes
- No npm dependencies; `package.json` has none. No `npm install` needed.
- No environment variables or secrets required.
- Node 20 `--watch` flag provides live reload without nodemon.
