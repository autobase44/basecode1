# Base44 Setup Notes

## Overview
Minimal Node.js web app (`server.js`) with zero dependencies and no database. Uses only `node:http`.

## Running
- `docker compose -f docker-compose.base44.yml up -d --build`
- App listens on port 3000, serves `/` (HTML page) and `/health` (JSON).
- Live reload via Node's built-in `--watch` flag — edits to `server.js` restart the process automatically.

## Verification
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"
- `curl http://localhost:3000/health` → `{"status":"ok"}`

## No Secrets Required
No external services, no environment variables beyond `PORT`, no database.
