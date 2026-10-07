# AGENTS.md

## Project: base-code-e2e

Minimal Node.js web app (single `server.js`, no npm dependencies, no database, no external services).

### Setup
- `docker compose -f docker-compose.base44.yml up -d` brings up the app on port 3000.
- The container bind-mounts the repo source, so edits to `server.js` require a container restart (`docker compose -f docker-compose.base44.yml restart web`) — there is no live-reload dev server.
- No environment variables or secrets are required to boot.

### Verification
- `GET /` returns the HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.
