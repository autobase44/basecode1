# Base44 Setup Notes

## Project
Minimal Node.js web app (no dependencies, no database, no external services).

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App serves on port 3000; health check at `/health` returns `{"status":"ok"}`.
- No live-reload dev server — after editing `server.js`, call `reload_preview` to refresh.

## Secrets
None required. The app boots with no environment variables beyond `PORT`.
