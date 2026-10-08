# Base44 Dev Environment

## Overview
Minimal Node.js web app (no dependencies, no database, no external services).
Single file `server.js` serves an HTML page at `/` and JSON at `/health`.

## Running
```bash
docker compose -f docker-compose.base44.yml up -d
```
- App runs from bind-mounted source on `node:20-alpine` (no rebuild needed for edits).
- Port 3000 is the web entry point.
- Healthcheck: `GET /health` → `{"status":"ok"}`

## Verification
- `curl http://localhost:3000/` shows the page with heading "Base Code E2E".
- `curl http://localhost:3000/health` returns `{"status":"ok"}`.

## Notes
- No dependencies, no environment variables, no secrets required.
- The README says not to change the app content (tests depend on it).
