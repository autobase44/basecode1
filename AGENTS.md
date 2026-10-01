# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000 (mapped to host port 3000).
- Live reload via Node's built-in `--watch` flag — edits to `server.js` restart the server automatically.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Notes
- No secrets or external credentials required.
- No build step — `server.js` runs directly with `node`.
- The repo's own `Dockerfile` bakes source via `COPY`; the Base44 compose uses a bind mount instead so edits are reflected live.
