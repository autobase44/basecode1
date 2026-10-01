# Base44 Dev Environment

## Overview
Minimal Node.js web app (no dependencies, no database, no external services).
Single file `server.js` serves HTML on port 3000 and a JSON `/health` endpoint.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- App: http://localhost:3000
- Health: http://localhost:3000/health → `{"status":"ok"}`
- Uses `nodemon --legacy-watch` for live reload on bind-mounted source.

## Notes
- No `node_modules` — zero npm dependencies.
- No environment variables or secrets required.
- The README asks not to change the app's content (E2E test fixture).
