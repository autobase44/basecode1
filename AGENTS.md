# Base44 Setup Notes

## Project
Minimal Node.js HTTP server (no dependencies, no database, no external services). Single file `server.js` serves an HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000 (env `PORT`).
- No live-reload dev server — `server.js` is plain `node`. After edits, call `reload_preview` to refresh the preview.

## Health Check
- `GET /health` returns `{"status":"ok"}`.

## No Secrets Required
This app has no external service dependencies and needs no credentials.
