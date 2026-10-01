# Base44 Dev Environment

## Overview
Minimal Node.js web app (no dependencies, no database, no external services).
Single file `server.js` serves an HTML page at `/` and JSON at `/health`.

## Running
```bash
docker compose -f docker-compose.base44.yml up -d --build
```
App listens on port 3000. Health check: `GET /health` → `{"status":"ok"}`.

## Notes
- No live-reload dev server — `node server.js` is the only entrypoint. After editing `server.js`, call `reload_preview` (or `docker compose -f docker-compose.base44.yml restart web`) to see changes.
- No dependencies to install; `package.json` has none.
- No secrets or environment variables required.
- The README asks not to change the app's content — tests depend on it.
