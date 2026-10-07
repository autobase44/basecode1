# Base44 Dev Environment

## App
Minimal Node.js HTTP server (`server.js`), no dependencies, no database, no external services.

## Run
```
docker compose -f docker-compose.base44.yml up -d --build
```
App listens on port 3000. `GET /` serves the page; `GET /health` returns `{"status":"ok"}`.

## Live reload
Uses `node --watch server.js` — edits to `server.js` restart the server automatically.

## Verification
- `curl http://localhost:3000/` → HTML with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`
