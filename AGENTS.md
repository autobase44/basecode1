# Base44 Dev Environment

## Overview
Minimal Node.js app (`server.js`) — no dependencies, no env vars, no database.
Serves a static HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- Web entry point: host port 3000
- Healthcheck: `GET /health` → `{"status":"ok"}`

## Notes
- The repo's own `Dockerfile` bakes source via `COPY` (production build). The Base44 compose instead bind-mounts the source and runs `node server.js` directly so edits are picked up on container restart.
- No live-reload dev server exists (plain `node server.js`). After editing `server.js`, run `docker compose -f docker-compose.base44.yml restart web` then `reload_preview`.
- No external credentials required.
