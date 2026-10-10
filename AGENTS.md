# AGENTS.md

## Overview

Minimal zero-dependency Node.js HTTP server (`server.js`) used as a Base44 E2E test fixture.

- **No npm dependencies** — uses only `node:http`. No `npm install` needed.
- **No database, no external services, no secrets.**
- Serves a single HTML page at `/` and a JSON health check at `/health`.

## Running

```bash
docker compose -f docker-compose.base44.yml up -d
```

- Uses `node:20-alpine` with the source bind-mounted at `/app`.
- Runs `node --watch server.js` for live reload on file changes (Node 20+ built-in watch mode).
- Port 3000 is the user-facing entry point.

## Verifying

```bash
curl http://localhost:3000/         # HTML page with heading "Base Code E2E"
curl http://localhost:3000/health   # {"status":"ok"}
```
