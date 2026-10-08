# Base44 Setup Notes

## App Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no environment variables, and no external services.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build` (or just `up -d` since it uses a base image)
- App listens on port 3000, binds all interfaces (`::`).
- `GET /` returns the HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.

## Live Reload
This is a plain Node HTTP server with no file watcher. After editing `server.js`, restart the service:
`docker compose -f docker-compose.base44.yml restart app`, then call `reload_preview`.

## Secrets
None required.
