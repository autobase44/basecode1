# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services, no environment variables required.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App listens on port 3000 (configured via `PORT` env, defaults to 3000).
- Uses `node --watch server.js` for live reload of source changes.
- Source is bind-mounted at `/app`; edits appear without rebuilding the image.

## Health & Verification
- `GET /health` → `{"status":"ok"}`
- `GET /` → HTML page with heading "Base Code E2E"
- Compose healthcheck probes `http://localhost:3000/health`.

## Notes
- No `npm install` needed — `package.json` has zero dependencies.
- No secrets required.
