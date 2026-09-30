# AGENTS.md

## Project Overview
Minimal Node.js web app (no dependencies, no database, no env vars) used as a Base44 E2E test fixture.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- The container uses `node --watch server.js` for live reload on file changes.
- Source is bind-mounted at `/app`; edits to `server.js` are reflected immediately.

## Health
- `GET /health` returns `{"status":"ok"}`.
- `GET /` returns the HTML page with heading "Base Code E2E".

## Notes
- No `npm install` needed — zero dependencies.
- No external credentials required.
