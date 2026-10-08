# AGENTS.md

## What this app is

A minimal, dependency-free Node HTTP server (`server.js`) used as an E2E test
fixture. Do not change `server.js`, `package.json`, or the README content —
the external E2E tests depend on their exact content.

Endpoints:
- `GET /` → HTML page with heading "Base Code E2E" (`data-testid="e2e-marker"`)
- `GET /health` → `{"status":"ok"}`

## Running it here (Base44 sandbox)

- `docker compose -f docker-compose.base44.yml up -d --build`
- The repo's own `Dockerfile` is **not** used by the sandbox setup: it bakes the
  source via `COPY`, so edits would not appear. Instead compose runs the app
  from a plain `node:20-alpine` image with the repo bind-mounted at `/app` and
  `node --watch server.js`, so source edits live-reload.
- No dependencies, no lockfile, no database, no migrations, no environment
  variables, and no secrets are required. `BASE44_PREVIEW_MODE` is passed
  through to the service for platform parity but the app does not read it; there
  are no sandbox-only code overrides.

## Verifying it works

- `curl -fsS http://localhost:3000/health` → `{"status":"ok"}`
- `curl -fsS http://localhost:3000/` → HTML containing "Base Code E2E"
- Compose healthcheck hits `/health` with busybox `wget`.
