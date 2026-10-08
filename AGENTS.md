# Base44 Setup Notes

## App overview
Minimal Node.js web app (single `server.js`, no dependencies, no database, no external services).
Serves an HTML page at `GET /` and JSON at `GET /health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d --build
```
- Base image: `node:20-alpine` (plain runtime, not a prebuilt app image).
- Source is bind-mounted at `/app`; edits to `server.js` require a service restart
  (`docker compose -f docker-compose.base44.yml restart web`) since there is no
  live-reload dev server — then call `reload_preview`.
- Web entry point is on host port 3000.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E".
- `curl http://localhost:3000/health` → `{"status":"ok"}`.

## No secrets required
The app needs no environment variables or external credentials.
