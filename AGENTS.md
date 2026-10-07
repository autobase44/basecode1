# Base44 Setup Notes

## Overview
Minimal zero-dependency Node.js web app (`server.js`) using only `node:http`.
Serves an HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000 (mapped to host 3000).
- No dependencies to install — `package.json` has no dependencies.
- No environment variables, no database, no external credentials required.

## Live reload
The app is a plain `node server.js` process with no framework hot-reload.
After editing `server.js`, restart the service and call `reload_preview`:
`docker compose -f docker-compose.base44.yml restart app`

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`
