# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no external services.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000, serves `GET /` (HTML page) and `GET /health` (JSON `{"status":"ok"}`)
- Source is bind-mounted; no live-reload server — call `reload_preview` after edits to `server.js`

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML with heading "Base Code E2E"

## Notes
- No package manager lockfile; no `npm install` needed (zero dependencies)
- No secrets required
