# AGENTS.md

## Project overview

Minimal Node.js web app (no dependencies, no database). Single file `server.js` serves an HTML page at `/` and a JSON health check at `/health`. Runs on port 3000.

## Running in the sandbox

- `docker compose -f docker-compose.base44.yml up -d` starts the app with `node --watch` for live reload.
- Base image: `node:20-alpine`; source is bind-mounted at `/app`.
- No environment variables or secrets required.
- Health check: `GET /health` returns `{"status":"ok"}`.
