# AGENTS.md — Base44 sandbox notes

## What this is
Minimal, zero-dependency Node HTTP app (`server.js`) that serves one HTML page on
port 3000, plus `GET /health` returning `{"status":"ok"}`.
The repo's own `Dockerfile` bakes the source with `COPY` (a frozen, prebuilt
image) — **do not use it for the sandbox**; use `docker-compose.base44.yml`.

## Run it
```
docker compose -f docker-compose.base44.yml up -d --build
```
- `web` runs `node --watch server.js` straight from the bind-mounted checkout,
  so edits to `server.js` reload without a rebuild.
- No dependencies to install (no `package-lock.json`, no `node_modules`), no
  database, no environment variables, no secrets.
- Host port 3000 is the preview entry point.
- Sandbox override: `BASE44_PREVIEW_MODE` is passed through bare under
  `environment:` (no app code reads it here). Unset, nothing changes.

## Verify
- `curl -s localhost:3000/health` → `{"status":"ok"}`
- `curl -s localhost:3000/` → HTML containing "Base Code E2E"
- `docker compose -f docker-compose.base44.yml ps` → `web` healthy

## Don't change
This repo is a fixture for the Base44 Base Code E2E tests; its content
(heading "Base Code E2E", `/health` response, port 3000) is asserted by those
tests, so leave the app itself alone.
