# Base44 Setup Notes

## Project Overview

Minimal Node.js web app (no dependencies, no database, no environment variables). A single `server.js` serves an HTML page at `GET /` and a JSON health check at `GET /health`.

## Running in the Sandbox

- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- The compose uses `node:20-alpine` with the source bind-mounted at `/app` and `node --watch server.js` for live reload on edits.
- No secrets or external credentials are required.

## Verification

- `curl http://localhost:3000/` returns the page with heading "Base Code E2E".
- `curl http://localhost:3000/health` returns `{"status":"ok"}`.
