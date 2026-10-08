# Base44 Setup Notes

## Project

Minimal single-file Node.js web app (`server.js`) — no dependencies, no database, no environment variables required.

- `GET /` → HTML page with heading "Base Code E2E"
- `GET /health` → `{"status":"ok"}`

## Running

`docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.

The compose uses `node:20-alpine` with the source bind-mounted and `nodemon` for live-restart on file edits. No image rebuild is needed for code changes.

## Verification

- `curl http://localhost:3000/` → HTML with "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`
