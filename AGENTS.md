# Base44 Dev Environment

## Overview
Minimal Node.js HTTP fixture app (`server.js`). No dependencies, no database, no external services, no environment variables. The README says **do not change the app code** — E2E tests depend on its exact content.

## Running
```sh
docker compose -f docker-compose.base44.yml up -d
```
- Runs from bind-mounted source on `node:20-alpine` (not a prebuilt image).
- Port 3000 is the web entry point.
- No live-reload framework; call `reload_preview` after edits to `server.js`.

## Health
- `GET /health` → `{"status":"ok"}`
- `GET /` → HTML page with heading "Base Code E2E"

## Secrets
None required.
