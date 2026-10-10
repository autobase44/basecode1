# AGENTS.md

## Project Overview
Minimal Node.js web app (test fixture). Single file `server.js` using only `node:http` — no dependencies, no framework, no database, no environment variables.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Base image: `node:20-alpine`; source is bind-mounted at `/app`; no build step needed.
- No live-reload dev server (plain `node server.js`). After editing `server.js`, run `docker compose -f docker-compose.base44.yml restart app` then `reload_preview`.
- Health check: `GET /health` → `{"status":"ok"}`. Page: `GET /` → HTML with heading "Base Code E2E".

## Notes
- The app binds to all interfaces (IPv4+IPv6) so `localhost` healthchecks work.
- No secrets or external credentials required.
