# Base44 Dev Environment

## App overview
Minimal Node.js web app (no dependencies, no database, no env vars required).
Single file `server.js` serves a static HTML page at `/` and JSON at `/health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d --build
```
- Web entry point: host port 3000
- Health check: `GET /health` → `{"status":"ok"}`
- Source is bind-mounted; the container runs `node server.js` directly.
- No live-reload dev server (plain `node`); call `reload_preview` after edits so the user sees changes.

## Constraints
The repo is an E2E test fixture — do NOT change `server.js`, `package.json`, `Dockerfile`, or `README.md` content the tests depend on.
