# Base44 Dev Environment

## App
Minimal Node HTTP server (`server.js`) — no dependencies, no database, no env vars.
- `npm start` / `node server.js` → serves on PORT (default 3000)
- `GET /` → HTML page with heading "Base Code E2E"
- `GET /health` → `{"status":"ok"}`

## Running
`docker compose -f docker-compose.base44.yml up -d --build`
Source is bind-mounted; no live-reload (plain `node`), so call `reload_preview` after edits.

## Notes
- This is a test fixture; the README asks not to change app content.
- No secrets required.
