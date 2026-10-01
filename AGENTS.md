# Base44 Dev Notes

## Stack
- Plain Node.js HTTP server (`server.js`), no framework, no dependencies, no database.
- No `npm install` needed — uses only `node:` builtins.

## Running
- `docker compose -f docker-compose.base44.yml up -d` — bind-mounts the source into `node:20-alpine` and runs `node server.js` on port 3000.
- No live-reload dev server (plain `http.createServer`); restart the container after source edits, or call `reload_preview`.
- Healthcheck: `GET /health` → `{"status":"ok"}`.

## Secrets
- None required.
