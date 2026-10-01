# Base44 Dev Environment

## Overview
Minimal Node.js app (`server.js`) — a single-file HTTP server with no dependencies, no database, no external services. Serves an HTML page at `/` and JSON at `/health`.

## Running
```
docker compose -f docker-compose.base44.yml up -d --build
```
- Web service runs on host port 3000.
- Uses `nodemon` for live reload of `server.js` (installed globally at container startup).
- Source is bind-mounted; edits to `server.js` trigger automatic restart.

## Verification
- `GET /` → HTML page with heading "Base Code E2E"
- `GET /health` → `{"status":"ok"}`
- No environment variables or secrets required.
