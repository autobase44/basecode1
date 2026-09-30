# AGENTS.md

## Project
Minimal Node.js web app (`server.js`) with zero dependencies and no database. Serves a static HTML page at `/` and `{"status":"ok"}` at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node --watch server.js` for live reload on file changes (no build step, no framework).
- Source is bind-mounted; edits to `server.js` restart automatically.

## Health
- `GET /health` returns `{"status":"ok"}`.
- Compose healthcheck probes `http://localhost:3000/health`.

## Notes
- No environment variables, no secrets, no external services required.
- Node >=20 required (uses built-in `--watch`).
