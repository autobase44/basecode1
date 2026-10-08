# Base44 Setup Notes

## Overview
Minimal Node.js web app (`server.js`) with zero dependencies. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000 (mapped to host 3000).
- No database, no environment variables, no external services, no secrets required.

## Live Reload
This project has no dev server or file watcher — it runs `node server.js` directly. After editing `server.js`, call `reload_preview` to reflect changes in the preview.

## Verification
- `GET /` → HTML page with heading "Base Code E2E"
- `GET /health` → `{"status":"ok"}`
