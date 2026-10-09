# Base44 sandbox notes

This is a deliberately minimal fixture app (a single `server.js` HTTP server).
The README warns that E2E tests depend on its exact content — do not restyle or
reword the page, and keep the `e2e-marker` test id and the `/health` JSON shape.

## Running here

- `docker compose -f docker-compose.base44.yml up -d --build` serves the app on
  host port 3000.
- There are **no dependencies** (no `node_modules`) and no build step, so nothing
  is installed at startup.
- There is no framework dev server; the service runs `node --watch server.js` so
  edits to `server.js` restart the process. If a change does not appear, call
  `reload_preview`.

## Verification

- `curl -s localhost:3000/health` → `{"status":"ok"}`
- `curl -s localhost:3000/` → HTML containing `Base Code E2E`
- The compose healthcheck uses node's built-in `fetch` because `node:20-alpine`
  ships neither `curl` nor `wget`.

## Environment

No environment variables, secrets, or database are required.
