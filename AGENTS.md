# Base44 Dev Environment

This is a minimal Node.js app (`server.js`) with no dependencies, no database, and no external credentials.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- Web entry point: http://localhost:3000 (serves the page)
- Health check: http://localhost:3000/health → `{"status":"ok"}`

## Notes
- No live-reload dev server; the app is plain `node server.js`. After editing `server.js`, run `docker compose -f docker-compose.base44.yml restart web` and call `reload_preview`.
- Source is bind-mounted from the repo root into the container at `/app`.
- No secrets or environment variables are required to boot.
