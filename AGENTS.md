# Base44 Dev Environment

## App overview
Minimal zero-dependency Node.js HTTP server (`server.js`). No database, no external services, no secrets required.

- `GET /` — HTML page with heading "Base Code E2E"
- `GET /health` — returns `{"status":"ok"}`

## Running
```bash
docker compose -f docker-compose.base44.yml up -d
```
The compose file uses `node:20-alpine`, bind-mounts the source at `/app`, and runs `node server.js` on port 3000.

## No live reload
This project has no dev server / file watcher. After editing `server.js`, restart the container:
```bash
docker compose -f docker-compose.base44.yml restart app
```
Then call `reload_preview` so the preview iframe refreshes.

## Notes
- The README asks not to change the app's content (it's an E2E test fixture).
- No `npm install` needed — the app uses only `node:http`.
