# Base44 Setup Notes

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no environment variables. Serves a static HTML page at `/` and JSON at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node --watch server.js` for live reload on file changes (Node 20 built-in watcher; no nodemon needed).
- Source is bind-mounted; edits appear after the watcher restarts the process.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E".
- `curl http://localhost:3000/health` → `{"status":"ok"}`.

## Constraints
- The repo is a test fixture — do NOT modify `server.js`, `package.json`, or `README.md` content the tests depend on.
