# Base44 Setup Notes

## Overview
Minimal Node.js web app (`server.js`) with zero dependencies, no database, and no environment variables.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- Serves on port 3000; `GET /` shows the page, `GET /health` returns `{"status":"ok"}`.
- Source is bind-mounted; no live-reload server exists, so restart the `web` service after edits (`docker compose -f docker-compose.base44.yml restart web`).

## Verification
- `curl localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl localhost:3000/health` → `{"status":"ok"}`
