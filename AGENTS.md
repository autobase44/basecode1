# Base44 Setup Notes

## App Overview
Minimal Node.js web app (`server.js`) — no dependencies, no database, no external credentials.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App listens on port 3000, binds all interfaces (`::`).
- Health check: `GET /health` → `{"status":"ok"}`

## Dev Notes
- No live-reload dev server; the app is a plain `http.createServer`. After editing `server.js`, call `reload_preview` or restart the container (`docker compose -f docker-compose.base44.yml restart app`).
- Source is bind-mounted at `/app`; the `node:20-alpine` image runs `server.js` directly.
- No `npm install` needed — zero dependencies.

## Verification
- `curl http://localhost:3000/health` returns `{"status":"ok"}`
- `curl http://localhost:3000/` returns the HTML page with heading "Base Code E2E"
