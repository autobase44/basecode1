# Base44 Dev Environment

## App
Minimal Node.js HTTP server (`server.js`) — no dependencies, no database, no env vars, no secrets.
- `GET /` → HTML page with heading "Base Code E2E"
- `GET /health` → `{"status":"ok"}`

## Running
`docker compose -f docker-compose.base44.yml up -d` — uses `node:20-alpine` with the repo bind-mounted at `/app` (NOT the project's Dockerfile, which bakes code into an image). Port 3000.

## Live reload
This project has no live-reload dev server (`node server.js` only). Edits to `server.js` require `reload_preview` to appear in the preview, or restart the service: `docker compose -f docker-compose.base44.yml restart app`.

## Do not change app code
The README states the test fixture depends on its exact content — do not modify `server.js`, `package.json`, or `README.md`.
