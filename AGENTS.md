# Base44 Setup Notes

## Project Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000, bound to all interfaces (`::`).
- No dependencies to install, no database, no environment variables required.
- No live-reload dev server; changes require a container restart or `reload_preview`.

## Verification
- `curl http://localhost:3000/` returns HTML with heading "Base Code E2E".
- `curl http://localhost:3000/health` returns `{"status":"ok"}`.
