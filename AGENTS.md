# AGENTS.md

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies and no database. Serves a static HTML page at `/` and `{"status":"ok"}` at `/health` on port 3000.

## Running in the Base44 sandbox
- `docker compose -f docker-compose.base44.yml up -d` brings up the app on port 3000.
- Uses `node:20-alpine` with the source bind-mounted at `/app`; runs `node --watch server.js` for live reload on edits.
- No environment variables or external credentials required.
- Healthcheck probes `http://localhost:3000/health`.
- Verify: `curl http://localhost:3000/health` returns `{"status":"ok"}`.
