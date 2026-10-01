# Base44 Dev Environment

## App overview
Minimal Node.js HTTP server (`server.js`) — a Base44 E2E test fixture. No dependencies, no database, no environment variables required.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build` starts the app on port 3000.
- The container runs `node server.js` directly (no live-reload dev server exists for this project). After editing `server.js`, restart the `web` service or call `reload_preview`.
- `GET /` returns the HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.

## Notes
- The server binds `::` (IPv4 + IPv6), so `localhost` healthchecks work.
- No secrets or external credentials are needed.
