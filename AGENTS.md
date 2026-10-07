# Base44 Dev Environment

## What this is
Minimal Node.js HTTP fixture app (`server.js`) — no dependencies, no database, no env vars, no build step.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- The source is bind-mounted; `node server.js` runs directly (no file watcher).
- After editing `server.js`, restart the service and call `reload_preview` — there is no live reload.

## Verifying
- `curl http://localhost:3000/` returns the page with heading "Base Code E2E".
- `curl http://localhost:3000/health` returns `{"status":"ok"}`.

## Notes
- The README says not to change the app content (tests depend on it). Setup artifacts (compose, env json, this file) are additive.
