# AGENTS.md

## Project Overview
Minimal Node.js HTTP server (no framework, no dependencies, no database). Used as a Base44 Base Code E2E test fixture — **do not change `server.js` or `package.json`**; the tests depend on their exact content.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node --watch server.js` for live reload on file changes (Node 20 built-in watcher).
- Source is bind-mounted; edits appear without rebuilding the image.
- No environment variables or secrets required.

## Verification
- `GET /` returns the HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"`.
