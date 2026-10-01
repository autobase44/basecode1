# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies and no database.
Serves an HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on host port 3000.
- Source is bind-mounted; `nodemon` watches `server.js` for live reload.

## Verification
- `curl localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl localhost:3000/health` → `{"status":"ok"}`

## Notes
- No environment variables, no secrets, no external services required.
- The repo's own `Dockerfile` bakes source via `COPY` — do NOT use it for dev; use the compose file instead.
