# Base44 Dev Environment

Minimal Node.js app (`server.js`) — no dependencies, no database, no env vars required.

## Run
```
docker compose -f docker-compose.base44.yml up -d
```
App listens on port 3000. `GET /` serves the page; `GET /health` returns `{"status":"ok"}`.

## Notes
- Source is bind-mounted; `server.js` has no live-reload, so call `reload_preview` after edits.
- The README is a test fixture — do not change its content.
