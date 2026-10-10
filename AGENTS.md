# AGENTS.md

## Project Overview
Minimal Node.js web app (no dependencies, no database, no external services). Single file `server.js` serves an HTML page on port 3000 and a `/health` JSON endpoint.

## Setup
- Runtime: Node.js 20 (via `node:20-alpine` in `docker-compose.base44.yml`)
- No `npm install` needed — zero dependencies.
- Start: `docker compose -f docker-compose.base44.yml up -d`
- Source is bind-mounted; `node --watch server.js` provides live reload on file changes.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"

## Notes
- No environment variables or secrets required.
- The README says "don't change it" — this is a test fixture. Keep `server.js` and `package.json` as-is unless explicitly asked.
