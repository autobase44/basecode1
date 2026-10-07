# Base44 Setup Notes

## Overview
Minimal zero-dependency Node.js HTTP server (`server.js`) used as a Base Code E2E test fixture.
No database, no external services, no environment variables required.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App listens on port 3000, uses `node --watch` for live reload on file changes.
- Health check: `GET /health` → `{"status":"ok"}`
- Main page: `GET /` → HTML with heading "Base Code E2E"

## Notes
- The source is bind-mounted, so edits to `server.js` trigger an automatic restart via `node --watch`.
- No secrets or credentials needed.
