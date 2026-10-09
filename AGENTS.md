# Agent notes — base-code-e2e

Minimal Node HTTP fixture. Deliberately tiny: **do not change app content** — the Base44
base-code E2E tests assert on this exact page (`data-testid="e2e-marker"`, heading
"Base Code E2E") and on `GET /health` returning `{"status":"ok"}`.

## Running it here
- `docker compose -f docker-compose.base44.yml up -d --build`
- Web entry point: host port 3000 (`GET /`).
- `node --watch server.js` is the run command, with the repo bind-mounted at `/app`, so
  edits to `server.js` restart the process without a rebuild.
- No dependencies, no lockfile, no install step, no database, no environment variables,
  and no external services — so nothing to migrate, seed, or provide credentials for.
- The repo's own `Dockerfile` bakes source via `COPY` (production style); it is
  intentionally NOT used for the sandbox, which runs from the cloned source instead.

## Verifying it works
- `curl -s http://localhost:3000/health` → `{"status":"ok"}`
- `curl -s http://localhost:3000/ | grep 'Base Code E2E'`
- The healthcheck uses Node's global `fetch` (the alpine image has no `curl`).
