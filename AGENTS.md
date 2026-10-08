# Base44 Dev Environment

## Overview
Minimal zero-dependency Node.js app (`server.js`) serving a static HTML page on port 3000 and a health endpoint at `/health`. No database, no env vars, no external services.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- Uses `node --watch server.js` for live reload on file changes (Node 20 built-in, no extra dependencies).
- Source is bind-mounted at `/app`; edits appear without rebuilds.
- Healthcheck: `GET /health` → `{"status":"ok"}`

## Notes
- The README says "Please don't change it" — this is an E2E test fixture.
- No secrets or credentials needed.
