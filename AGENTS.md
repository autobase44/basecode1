# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000 (mapped to host port 3000).
- Source is bind-mounted at `/app`, so edits are picked up on container restart (no live-reload dev server exists).

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Notes
- No secrets, no external services, no migrations or seeds required.
- After editing `server.js`, run `reload_preview` (or restart the container) since there is no file watcher.
