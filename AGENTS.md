# Base44 Dev Environment

## Overview
Minimal Node.js app (single `server.js`) with zero dependencies, no database, and no environment variables. Serves a static HTML page at `/` and a JSON health check at `/health` on port 3000.

## Running
```bash
docker compose -f docker-compose.base44.yml up -d --build
```

## Notes
- The app uses only `node:http` — no `npm install` needed.
- No live-reload dev server; after editing `server.js`, call `reload_preview` to refresh.
- The README asks not to change the app content (E2E test fixture).
