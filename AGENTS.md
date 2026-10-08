# Base44 Setup Notes

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no env vars, no database.
- `GET /` → HTML page with heading "Base Code E2E"
- `GET /health` → `{"status":"ok"}`

## Running in the sandbox
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node:20-alpine` with the source bind-mounted at `/app` and `node --watch` for live reload on file changes.
- No external credentials or secrets required.
- Healthcheck: `wget -qO- http://localhost:3000/health` (wget is available in the alpine image).
