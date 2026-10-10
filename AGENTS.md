# Base44 setup notes

## What this is
A dependency-free Node HTTP server (`server.js`) that serves one static page and
`GET /health` → `{"status":"ok"}`. No env vars, no database, no external services.

## Running it here
`docker-compose.base44.yml` runs `node:20-alpine` with the repo bind-mounted at
`/app` and `node --watch server.js` so edits reload automatically. Host port 3000
is the public entry point.

```sh
docker compose -f docker-compose.base44.yml up -d --build
curl -s localhost:3000/health          # {"status":"ok"}
```

`BASE44_PREVIEW_MODE` is passed through but the app does not branch on it; there
are no sandbox-only code overrides.

## Verifying
- `curl -s localhost:3000/` contains the heading "Base Code E2E".
- `curl -s localhost:3000/health` returns `{"status":"ok"}`.

Per the README this repo is an E2E test fixture: don't change `server.js` or its
served content.
