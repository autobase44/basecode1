# AGENTS.md

## What this is
A minimal, zero-dependency Node HTTP app (`server.js`): `GET /` serves a static page
(heading "Base Code E2E"), `GET /health` returns `{"status":"ok"}`.

The README asks that the app's content stay exactly as-is (Base44 E2E fixture), so
keep changes to the app content minimal.

## Running it (Base44 sandbox)
```bash
docker compose -f docker-compose.base44.yml up -d --build
```
- Web entry point: host port **3000** (`http://localhost:3000`), health: `/health`.
- Single service (`web`) on a plain `node:22` runtime image with the repo bind-mounted
  at `/app` — always the cloned source, never a prebuilt image.
- Run command is `node --watch server.js`: Node's built-in watcher restarts on file
  changes, so edits show up without a rebuild (verified working over the bind mount).
- No dependencies to install, no database, no migrations, no environment variables,
  and no external service credentials (`secrets: []`).
- No sandbox-only config overrides are needed: the server does no Host/Origin checking,
  so the preview host and origin are accepted as-is and `BASE44_PREVIEW_MODE` is unused.

## Verifying it works
```bash
curl -s http://localhost:3000/health   # {"status":"ok"}
curl -s http://localhost:3000/ | grep e2e-marker   # page renders
docker compose -f docker-compose.base44.yml ps     # web: healthy
```

## Notes
- `Dockerfile` in the repo root is the original production build (bakes source) and is
  intentionally not used by the Base44 setup.
- There are no tests in this repo.
