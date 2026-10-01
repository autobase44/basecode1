# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no environment variables.
Serves a static HTML page at `/` and a JSON health check at `GET /health`.

## Running
```bash
docker compose -f docker-compose.base44.yml up -d --build
```
The app listens on port 3000. The compose file bind-mounts the source and runs `nodemon` so edits to `server.js` hot-reload without a rebuild.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Notes
- The README asks not to change the app files — the E2E test fixture depends on exact content.
- No external credentials or secrets are needed.
