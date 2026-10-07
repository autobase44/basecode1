# Base44 Dev Environment

## Overview
Minimal Node.js web app (`server.js`) with zero dependencies, no database, and no external services.

## Running
```bash
docker compose -f docker-compose.base44.yml up -d --build
```
The app listens on port 3000 and serves:
- `GET /` — HTML page with heading "Base Code E2E"
- `GET /health` — returns `{"status":"ok"}`

## Notes
- No live-reload dev server; `server.js` is plain `http.createServer`. After editing source, call `reload_preview` to reflect changes.
- No environment variables or secrets required.
- The server binds `::` (IPv4+IPv6) so `localhost` healthchecks work from within the container.
