# AGENTS.md

## Overview

Minimal Node.js HTTP server (`server.js`) with zero dependencies and no database. Serves a static HTML page at `/` and JSON at `/health`.

## Running

- `docker compose -f docker-compose.base44.yml up -d` — starts the app on port 3000.
- The server binds all interfaces (`::`), so it is reachable from the preview proxy.
- No environment variables or secrets required.
- No build step; `node server.js` runs directly from the bind-mounted source.

## Verification

- `GET /` returns the page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.
