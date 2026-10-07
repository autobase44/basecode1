# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (no dependencies, no database). Serves a static page at `/` and a JSON health check at `/health` on port 3000.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts the app with live reload (nodemon watches `server.js`).
- App is served from bind-mounted source at `/app`; edits to `server.js` hot-reload automatically.
- No secrets, environment variables, or external services required.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- The README warns not to change app content — tests depend on exact content.

## Notes
- The app has no `package.json` dependencies; nodemon is installed at container startup via `npm install -g nodemon`.
- Server binds to `::` (all interfaces), so it accepts the preview proxy's hostname without configuration.
