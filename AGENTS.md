# Base44 Dev Environment

## App
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no external credentials.
Serves an HTML page at `/` and JSON at `/health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d
```
- Base image: `node:20-alpine`, source bind-mounted at `/app`, runs `node server.js`.
- No live-reload watcher; after editing `server.js`, restart the service and reload the preview:
  `docker compose -f docker-compose.base44.yml restart web`

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
