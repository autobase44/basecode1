# Base Code E2E — Base44 Dev Notes

Minimal Node.js HTTP server (`server.js`), no dependencies, no database, no env vars.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Source is bind-mounted into a `node:20-alpine` container; `node server.js` runs directly.
- No live-reload dev server — after editing `server.js`, restart the container (`docker compose -f docker-compose.base44.yml restart web`) and call `reload_preview`.

## Health
- `GET /health` → `{"status":"ok""`
- `GET /` → HTML page with heading "Base Code E2E"

## Notes
- No `npm install` needed (zero dependencies).
- No external secrets required.
