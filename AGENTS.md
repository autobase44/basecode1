# AGENTS.md

## Project

Minimal Node.js HTTP fixture app (`server.js`, no dependencies, no database, no external services).

## Running here

- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node:20-alpine` with the source bind-mounted at `/app` and `node --watch server.js` for live reload on file changes.
- Healthcheck: `GET /health` → `{"status":"ok"}`.
- No secrets or environment variables required (only `PORT`, defaulting to 3000).
