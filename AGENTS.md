# Base44 Dev Environment

## Overview
Minimal Node.js app (`server.js`) — no dependencies, no database, no external services.
Serves a static HTML page on `/` and JSON on `/health`. README says tests depend on
exact content — do not modify `server.js` or `package.json`.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- Image: `node:20-alpine` (runtime base, not a prebuilt app image)
- Source bind-mounted at `/app`; runs `node server.js` (no live-reload framework)
- Port 3000 mapped to host
- Healthcheck: `GET /health` → `{"status":"ok"}`

## Notes
- No live-reload dev server (raw `http` module). After editing `server.js`, run
  `docker compose -f docker-compose.base44.yml restart app` then `reload_preview`.
- No secrets or environment variables required.
