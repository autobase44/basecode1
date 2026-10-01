# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, and no external services. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000 (mapped to host port 3000).
- Source is bind-mounted; `node --watch` restarts on file changes (no rebuild needed).
- No environment variables, secrets, migrations, or seeds required.

## Verification
- `GET /` → HTML page with heading "Base Code E2E"
- `GET /health` → `{"status":"ok"}`
