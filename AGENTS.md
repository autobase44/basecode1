# AGENTS.md

Notes for running this repo in the Base44 sandbox.

## What this app is

A deliberately minimal Node HTTP server (`server.js`, no dependencies, no
database, no environment variables). It is an E2E test fixture — the README asks
that its content (the heading "Base Code E2E", the `/health` JSON) not be
changed, since the tests depend on it.

## Running it here

```bash
docker compose -f docker-compose.base44.yml up -d --build
```

- Serves the page at `/` and `{"status":"ok"}` at `/health` on host port 3000.
- Runs `node --watch server.js` from the bind-mounted source, so editing
  `server.js` restarts the server automatically — no rebuild needed.
- There is no dependency install step (the project has no dependencies and no
  lockfile), and no secrets are required.

## Gotcha

Do **not** run the repo's own `Dockerfile` for development: it uses `COPY . .`
and bakes the source into the image, so edits to `server.js` would never reach
the preview. Always use `docker-compose.base44.yml`.

## Verifying it works

```bash
curl -s http://localhost:3000/health          # -> {"status":"ok"}
curl -s http://localhost:3000/ | grep 'Base Code E2E'
docker compose -f docker-compose.base44.yml ps   # web should be (healthy)
```

There are no tests configured in this repo.
