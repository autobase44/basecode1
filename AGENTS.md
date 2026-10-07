# Base44 Development Notes

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Setup
- No `npm install` needed — the app uses only `node:http`.
- No environment variables, no database, no external services.
- Runs via `docker compose -f docker-compose.base44.yml up -d --build`.
- Live reload: Node's built-in `--watch` flag restarts the server on file changes.

## Verification
- `GET /` → HTML page with heading "Base Code E2E".
- `GET /health` → `{"status":"ok"}`.
