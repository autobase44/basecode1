# Base44 Dev Environment

This is a minimal Node.js HTTP server fixture (`server.js`) with no dependencies, no environment variables, and no database.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on host port 3000.
- The compose service bind-mounts the repo source, so edits to `server.js` require a `reload_preview` (no live-reload dev server is used — plain `node server.js`).
- No external secrets or credentials are needed.

## Verification
- `GET /` returns the page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.
- Healthcheck in compose probes `http://localhost:3000/health`.
