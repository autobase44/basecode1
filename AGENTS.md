# Base44 Dev Environment

## What this is
Minimal Node.js HTTP server fixture (`server.js`) — no dependencies, no database, no external services, no secrets.

## Running
`docker compose -f docker-compose.base44.yml up -d` — uses `node:20-alpine` with the source bind-mounted at `/app`. Serves on port 3000.

## Notes
- No live-reload framework; after editing `server.js`, run `reload_preview` (or `docker compose restart web`) to see changes.
- Health check: `GET /health` → `{"status":"ok"}`.
- The server binds `::` (dual-stack) so `localhost` healthchecks work inside the container.
