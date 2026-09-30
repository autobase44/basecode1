# Base44 Dev Notes

## Project
Minimal Node.js web app (no dependencies, no database, no env vars). Single file `server.js` serves:
- `GET /` — HTML page with heading "Base Code E2E"
- `GET /health` — returns `{"status":"ok"}`

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- Preview on host port 3000.
- Live reload via `node --watch server.js` (Node 20+ built-in). Edit `server.js` and save; the server restarts automatically.

## Verifying
- `curl http://localhost:3000/` returns the HTML page.
- `curl http://localhost:3000/health` returns `{"status":"ok"}`.

## No secrets required
The app has no external integrations and no required environment variables.
