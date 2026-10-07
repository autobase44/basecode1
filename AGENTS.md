# Base44 Dev Environment

## Project
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external services.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App binds port 3000; `GET /` serves the page, `GET /health` returns `{"status":"ok"}`.
- Source is bind-mounted at `/app`; there is no live-reload dev server (plain `node server.js`), so edit `server.js` then `docker compose restart web` and call `reload_preview`.

## No secrets required
The app needs no external credentials.
