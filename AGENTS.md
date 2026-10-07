# AGENTS.md

## Project overview
Minimal Node.js HTTP server (no dependencies, no framework). `server.js` serves a static HTML page at `/` and a JSON health check at `/health`.

## Running in the sandbox
- `docker compose -f docker-compose.base44.yml up -d` — starts the app on port 3000.
- The source is bind-mounted, so edits to `server.js` require a container restart (`docker compose -f docker-compose.base44.yml restart web`) since there is no live-reload dev server.
- No environment variables, secrets, or database needed.

## Verification
- `curl http://localhost:3000/health` → `{"status":"ok"}`
- `curl http://localhost:3000/` → HTML page with heading "Base Code E2E".
