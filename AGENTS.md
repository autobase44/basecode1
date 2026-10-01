# Base44 Dev Environment

## Overview
Minimal Node.js web app (plain `http` module, no framework, no dependencies, no database).
- `server.js` serves `GET /` (HTML page) and `GET /health` (`{"status":"ok"}`).
- No environment variables or external credentials required.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- Uses `node:20-alpine` with the repo bind-mounted at `/app`.
- Runs via `nodemon --watch server.js` so edits to `server.js` auto-restart the process.
- Web entry point on host port 3000; healthcheck probes `http://localhost:3000/health`.

## Notes
- The README says the E2E tests depend on exact content — do not change `server.js` or `package.json` content unless asked.
- No live-reload of the browser (plain HTML); call `reload_preview` after server-side changes.
