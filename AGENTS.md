# Base44 dev environment

This is a minimal, dependency-free Node.js HTTP server (`server.js`) used as an E2E fixture.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — starts the app on port 3000 with `node --watch` for live reload.
- No dependencies to install (`package.json` has none), no database, no environment variables required.
- Source is bind-mounted at `/app`, so edits to `server.js` hot-reload without a rebuild.

## Verification
- `GET /` returns the HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}` (used by the compose healthcheck).

## Notes
- The server binds `::` (all interfaces, IPv4+IPv6), so `localhost` healthchecks work.
- Do not change the app's behavior — the E2E tests depend on its exact content.
