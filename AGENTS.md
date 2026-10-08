# Base44 Setup Notes

## Overview
Minimal Node.js web app (no dependencies, no database, no external services).
Single file `server.js` serves an HTML page at `/` and JSON at `/health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- Uses `node:20-alpine` with the source bind-mounted at `/app`.
- Runs `node --watch server.js` for live reload on file changes.
- Port 3000 is the web entry point.
- Healthcheck probes `GET /health` (returns `{"status":"ok"}`).

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Notes
- No environment variables, secrets, or external credentials required.
- No `npm install` needed — the app uses only Node.js built-in modules.
