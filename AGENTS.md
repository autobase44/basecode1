# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (no framework, no dependencies, no database). Serves a static HTML page at `/` and `{"status":"ok"}` at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node:20-alpine` with the source bind-mounted at `/app`; `nodemon` watches `server.js` for live reload.
- No external credentials or environment variables required.

## Verifying
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"

## Notes
- The repo's own `Dockerfile` bakes source via `COPY` (production build) — not used for dev. The Base44 compose bind-mounts source instead so edits are live.
- The README warns against changing app content; tests depend on it.
