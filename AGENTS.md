# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no env vars, no database.
`npm start` runs `node server.js`, serving `GET /` (HTML page) and `GET /health` (`{"status":"ok"}`).

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- Source is bind-mounted into the `node:20-alpine` container; edit `server.js` then restart the service (`docker compose -f docker-compose.base44.yml restart web`) since there is no live-reload dev server.
- After a code change, call `reload_preview` so the user sees it.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"

## Notes
- This is an E2E test fixture; the tests depend on its exact content. Avoid changing the page text or routes unless asked.
- No external credentials or secrets are required.
