# Base44 Dev Environment

## Overview
Minimal single-file Node.js web app (`server.js`) — no dependencies, no database, no external services.

## Running
```sh
docker compose -f docker-compose.base44.yml up -d
```
- Web service on port 3000 (`GET /` shows the page, `GET /health` returns `{"status":"ok"}`)
- Source is bind-mounted; `nodemon` watches `server.js` for live reload
- No secrets or environment variables required

## Notes
- The README says not to change the app content — E2E tests depend on it.
- The project's own `Dockerfile` bakes source via `COPY` (production-style); the Base44 compose uses a plain `node:20-alpine` image with bind-mount instead so edits are visible without rebuilds.
