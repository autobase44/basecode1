# Base44 Dev Environment

## Overview
Minimal single-file Node.js HTTP server (`server.js`), no dependencies, no database, no external credentials.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — serves on port 3000.
- Health check: `GET /health` → `{"status":"ok"}`.
- The compose uses `node:20-alpine` with the source bind-mounted at `/app`; edits to `server.js` require a container restart (no live-reload dev server in this project). Call `reload_preview` after changes.

## Notes
- `README.md` warns not to change the app's content — E2E tests depend on the exact page output (heading "Base Code E2E").
- No secrets or env vars are required to boot.
