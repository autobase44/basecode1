# Base44 Dev Environment

## App overview
Minimal single-file Node.js HTTP server (`server.js`). No dependencies, no database, no external services.

- `GET /` — HTML page with heading "Base Code E2E"
- `GET /health` — returns `{"status":"ok"}`

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000 (mapped to host 3000).
- Uses `node --watch` for live reload on edits to `server.js`.

## Verification
- `curl http://localhost:3000/` returns the page.
- `curl http://localhost:3000/health` returns `{"status":"ok"}`.

## Notes
- No external credentials or secrets required.
- No package dependencies to install (`npm install` not needed).
