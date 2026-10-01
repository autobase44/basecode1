# Base44 Setup Notes

## Overview
Minimal Node.js HTTP server (no framework, no dependencies, no database).
Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App listens on port 3000 inside the container.
- No environment variables or secrets required.
- No build step — `node server.js` runs directly from the bind-mounted source.

## Live reload
This project uses a plain `http.createServer` with no file watcher.
After editing `server.js`, restart the service:
`docker compose -f docker-compose.base44.yml restart web`
then call `reload_preview`.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`
