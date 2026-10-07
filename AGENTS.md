# Base Code E2E — Base44 setup notes

Minimal Node.js fixture app (single `server.js`, no dependencies, no database, no external services).

## Run
- `docker compose -f docker-compose.base44.yml up -d`
- App served on host port 3000; healthcheck probes `GET /health` (`{"status":"ok"}`).
- Base image `node:20-alpine`; source bind-mounted at `/app`; runs `node server.js` (no live-reload — plain HTTP server; call `reload_preview` after edits).

## No secrets required
The app reads only `PORT` (default 3000). No external credentials needed.
