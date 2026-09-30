# Base44 Dev Environment

## Overview
Minimal Node.js HTTP server (`server.js`) with zero dependencies, no database, no external services. Serves a static HTML page at `/` and a JSON health check at `/health`.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- Web entry point: port 3000
- Health check: `GET /health` → `{"status":"ok"}`
- Source is bind-mounted; there is **no live-reload dev server** (plain `node server.js`), so after editing `server.js` you must restart the container (`docker compose -f docker-compose.base44.yml restart web`) and call `reload_preview`.

## Secrets
None required. No external services, no database, no environment variables needed.
