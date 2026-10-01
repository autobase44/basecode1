# Base44 Dev Environment

## Overview
Minimal Node.js web app (no dependencies, no database, no external services).
Single file: `server.js` — serves an HTML page on `GET /` and `{"status":"ok"}` on `GET /health`.

## Running
```bash
docker compose -f docker-compose.base44.yml up -d --build
```
- App listens on port 3000.
- Uses `node --watch server.js` for live reload on file changes.
- Healthcheck: `GET /health` returns `{"status":"ok"}`.

## Notes
- No `npm install` needed — zero dependencies.
- No environment variables or secrets required.
- Node >=20 required (uses built-in `--watch` mode).
