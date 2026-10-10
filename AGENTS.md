# AGENTS.md

## Project Overview
Minimal Node.js web app (no dependencies, no database, no external services). Single file `server.js` serves an HTML page on port 3000 and a `/health` JSON endpoint.

## Setup
- Run with `docker compose -f docker-compose.base44.yml up -d`.
- No `npm install` needed — the app uses only Node.js built-in modules.
- No environment variables or secrets required.

## Verification
- `GET /` returns the HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.

## Notes
- The README says not to change the app — tests depend on its exact content.
- No live-reload dev server; use `reload_preview` after editing `server.js`.
