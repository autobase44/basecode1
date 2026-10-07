# Base44 Dev Environment

This is a minimal Node.js app (no dependencies, no database, no external services).

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- The compose uses `node --watch server.js` for live reload of source edits (no dev server, no build step).
- Source is bind-mounted at `/app`; edits to `server.js` trigger an automatic restart.

## Verification
- `GET /` returns the page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.

## Notes
- No secrets or environment variables are required to boot.
- The repo's own `Dockerfile` bakes source via `COPY` (production-style); the Base44 compose avoids it so edits are visible live.
