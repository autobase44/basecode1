# Base44 Dev Environment

## Overview
Minimal zero-dependency Node.js HTTP app (`server.js`) used as an E2E test fixture.
No database, no external services, no environment variables required.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- The source is bind-mounted and run via `node --watch server.js` (Node 20 built-in file watcher) for live reload.
- `GET /` returns the HTML page; `GET /health` returns `{"status":"ok"}`.

## Notes
- Do not change the app content: the E2E tests depend on the exact heading "Base Code E2E".
- No secrets or credentials are needed.
