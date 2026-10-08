# Base44 Dev Environment

## Project

Minimal Node.js web app (`server.js`) — no dependencies, no database, no external services.
Serves an HTML page at `/` and JSON at `/health` on port 3000.

## Running

```sh
docker compose -f docker-compose.base44.yml up -d --build
```

The app is a plain `node server.js` process (no live-reload dev server).
After editing `server.js`, restart the container or call `reload_preview`:

```sh
docker compose -f docker-compose.base44.yml restart web
```

## Verification

- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## Notes

- No `npm install` needed — zero runtime dependencies.
- No secrets or environment variables required beyond `PORT` (defaults to 3000).
