# AGENTS.md

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no external services. Used as a Base44 E2E test fixture.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- Serves on port 3000. `GET /` returns the HTML page; `GET /health` returns `{"status":"ok"}`.
- Runs from a bind-mounted `node:20-alpine` image — edits to `server.js` require a container restart (no live-reload watcher; the project has no dev dependencies).

## Notes
- No environment variables or secrets required.
- No test suite.
