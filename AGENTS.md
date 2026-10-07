# Base44 Dev Environment

Minimal Node.js HTTP server fixture (`server.js`). No dependencies, no database, no environment variables, no build step.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- Web entry point on host port 3000; healthcheck at `GET /health` → `{"status":"ok"}`.
- Source is bind-mounted into the `node:20-alpine` container; the app runs via `node server.js` (no live-reload watcher — call `reload_preview` after edits to `server.js`).

## Notes
- The server binds `::` (dual-stack IPv4+IPv6), so `localhost` healthchecks work.
- No external credentials required.
