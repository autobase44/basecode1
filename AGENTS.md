# Agent notes

## Running in the Base44 sandbox
```bash
docker compose -f docker-compose.base44.yml up -d --build
```
- Service `app` runs `node --watch server.js` from a bind-mounted copy of the repo on
  `node:20-alpine`, so source edits restart the server with no image rebuild.
- Web entry point is host port **3000** (`GET /` = page, `GET /health` = `{"status":"ok"}`).
- No dependencies, no lockfile, no database, no environment variables.
- The server binds all interfaces (no host arg), so it is reachable behind the preview proxy.

## Quirks
- `server.js` and `Dockerfile` are a fixed E2E test fixture — the README explicitly asks
  that they not be changed. Keep edits out of the fixture's markup and routes.
- The repo `Dockerfile` bakes source with `COPY` (production image); do **not** use it for the
  sandbox. The Base44 compose deliberately does not build it.

## Verifying
```bash
curl -s http://localhost:3000/health          # -> {"status":"ok"}
curl -s http://localhost:3000/ | grep -o 'data-testid="e2e-marker"'
```
