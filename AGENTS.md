# Base44 Setup Notes

## Project

Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external credentials. Serves a static HTML page at `/` and `{"status":"ok"}` at `/health`.

## Running

- `docker compose -f docker-compose.base44.yml up -d` brings up the app on port 3000.
- Uses `node:20-alpine` with the source bind-mounted at `/app`; runs `node server.js` directly (no live-reload dev server exists — call `reload_preview` after edits).
- Healthcheck: `wget -qO- http://localhost:3000/health`.

## Notes

- No `npm install` needed — the app uses only `node:http`.
- No environment variables or secrets required.
