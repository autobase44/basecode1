# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (no dependencies, no database, no external services).
Entry point: `server.js` — serves an HTML page at `/` and JSON at `/health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d --build
```
The container uses `node --watch server.js` for live reload on file changes.

## Verification
- `GET /` returns HTML with heading "Base Code E2E"
- `GET /health` returns `{"status":"ok"}`

## Notes
- No environment variables or secrets required.
- No `npm install` needed — the app uses only Node built-ins.
