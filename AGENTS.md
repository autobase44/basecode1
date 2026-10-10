# AGENTS.md

## Project Overview
Minimal Node.js web app (no dependencies, no database, no external services).
Single file `server.js` serves an HTML page at `/` and JSON at `/health`.

## Setup
- Runtime: Node.js >= 20 (via `node:20-alpine` in Docker Compose)
- No `npm install` needed — zero dependencies.
- Dev command: `node --watch server.js` (live reload on file changes).
- Port: 3000.

## Verify
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E"

## Notes
- The README says not to change app content (it's an E2E test fixture).
- No secrets or environment variables required.
