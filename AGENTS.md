# Base44 Dev Environment

Minimal single-file Node.js HTTP server (`server.js`) with no dependencies, no database, and no environment variables.

## Running
- `docker compose -f docker-compose.base44.yml up -d` starts the app on port 3000.
- Uses `node:20-alpine` with the source bind-mounted at `/app` and `node --watch server.js` for live reload on file changes.
- No build step, no dependency install, no migrations/seeds.

## Verification
- `GET /` returns the HTML page with heading "Base Code E2E".
- `GET /health` returns `{"status":"ok"}`.
- Compose healthcheck probes `http://localhost:3000/health`.

## Notes
- The repo's own `Dockerfile` bakes source via `COPY` (production-style) and is not used for dev — edits would be invisible. The Base44 compose bind-mounts source instead.
- No external credentials are required.
