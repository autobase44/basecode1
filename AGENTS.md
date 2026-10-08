# Working on this repo (Base44 sandbox)

## What this is
A zero-dependency Node 20 fixture app (`server.js`) used by Base44 Base Code E2E
tests. The README asks that its content stay byte-for-byte as-is: tests assert on
the heading `Base Code E2E` and on `GET /health` returning `{"status":"ok"}`.
Do not refactor, "improve", or reformat `server.js` / `package.json`.

## Running it
```bash
docker compose -f docker-compose.base44.yml up -d --build
```
- Web entry point: host port **3000** (bound `0.0.0.0`; the server itself has no
  host allowlist, so it accepts the preview proxy's forwarded `Host` header as-is).
- Health: `GET /health` → `{"status":"ok"}`.

## Non-obvious setup notes
- The repo's own `Dockerfile` is **not** used by the sandbox: it `COPY`s the source
  into a production image, so edits would not appear. `docker-compose.base44.yml`
  instead runs `node:20-alpine` with the repo bind-mounted at `/app`.
- There is no dev server and no dependencies, so live reload comes from Node's
  built-in `node --watch server.js` (restarts the process on file change). Verified
  to fire through the Docker bind mount, so no polling is needed.
- No environment variables, no secrets, no database, no migrations. Nothing to
  configure for local infra.

## Verifying a change
```bash
curl -s -o /dev/null -w '%{http_code}\n' http://localhost:3000/health   # expect 200
curl -s http://localhost:3000/ | grep 'Base Code E2E'
```
