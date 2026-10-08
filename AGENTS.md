# Base44 Setup Notes

## Project
Minimal Node.js web app (`server.js`) — no dependencies, no database, no external services, no environment variables required.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- App served on port 3000; health check at `GET /health` → `{"status":"ok"}`
- Source is bind-mounted; the app runs `node server.js` directly (no file watcher). After editing `server.js`, restart the container or call `reload_preview`.

## Verification
- `curl http://localhost:3000/health` returns `{"status":"ok"}`
- `curl http://localhost:3000/` returns the HTML page with heading "Base Code E2E"
