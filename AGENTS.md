# Base44 Setup Notes

## Project Overview
Minimal Node.js web app (test fixture). Single `server.js` file using only `node:http` — no dependencies, no database, no environment variables.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- The compose uses `node:20-alpine` with the source bind-mounted at `/app`.
- No live-reload dev server (plain `http.createServer`); call `reload_preview` after edits to refresh the preview.

## Health Check
- `GET /health` returns `{"status":"ok"}`.
- `GET /` returns the HTML page with heading "Base Code E2E".

## No Secrets Required
The app has no external service dependencies.
