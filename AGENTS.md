# Base44 Agent Notes

## Project Overview
Minimal Node.js web app (plain `node:http`, no framework, no dependencies).
Serves a static HTML page at `/` and a JSON health check at `/health`.

## Setup
- **Runtime:** Node.js 20+ (via `node:20-alpine` in `docker-compose.base44.yml`)
- **Start:** `docker compose -f docker-compose.base44.yml up -d`
- **Live reload:** `node --watch server.js` restarts the server when `server.js` changes.
- **No dependencies to install** — the app uses only Node.js built-ins.
- **No environment variables, no database, no external secrets.**

## Verification
- `GET /` returns HTML with heading "Base Code E2E"
- `GET /health` returns `{"status":"ok"}`
- Preview is served on host port 3000.
