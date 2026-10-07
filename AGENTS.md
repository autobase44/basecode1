# Base44 Dev Environment

## Project Overview
Minimal Node.js web app (no dependencies, no database, no external services).
- `server.js` — single-file HTTP server using only `node:http`.
- `GET /` — HTML page with heading "Base Code E2E".
- `GET /health` — returns `{"status":"ok"}`.

## Running
```bash
docker compose -f docker-compose.base44.yml up -d --build
```
The compose file bind-mounts the repo source and runs `nodemon` for live reload of `server.js`. No environment variables or secrets are required.

## Verification
- `curl http://localhost:3000/` → HTML page with "Base Code E2E" heading.
- `curl http://localhost:3000/health` → `{"status":"ok"}`.

## Notes
- The app has zero npm dependencies; `package.json` lists none.
- `server.js` binds to all interfaces (no host specified), so `localhost` healthchecks work.
- The README warns not to change the app content — E2E tests depend on it.
