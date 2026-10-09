# AGENTS.md

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no environment variables beyond `PORT`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- The compose uses `node --watch` for live reload on file changes.
- `GET /` returns the HTML page; `GET /health` returns `{"status":"ok"}`.

## Notes
- The app binds to all interfaces (`::`) so `localhost` healthchecks work.
- No secrets or external credentials required.
- The README states tests depend on exact file contents — avoid changing `server.js` or `package.json` unless necessary.
