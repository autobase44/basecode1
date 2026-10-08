# Base44 Dev Environment

## Overview
Minimal Node.js web app (no dependencies, no database). Single file `server.js` serves an HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000 (mapped to host 3000).
- No environment variables or secrets required.
- No `npm install` needed — the app uses only Node.js built-in modules.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Notes
- The app binds to all interfaces (`::`) so localhost healthchecks work.
- Source is bind-mounted; edits to `server.js` require a container restart (no live-reload dev server).
